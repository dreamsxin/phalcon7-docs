教程 2：Introducing INVO（Tutorial 2: Introducing INVO）
========================================================

在第二部分，我们将会说明一个完整的应用用来加深Phalcon的开发。
INVO是我们创建的一个程序样本。INVO是一个简单的用来允许用户生成发票的网站，并且可以做其他的任务，比如管理他们的客户或者产品。你可以从 Github_ 中复制它的代码。

同样，INVO使用 `Bootstrap`_ 做的前端框架。虽然这个应用不能生成发票，但是它仍然可以作为一个例子来理解框架是如何工作的。

项目结构（Project Structure）
-----------------------------
一旦你从你的文档根目录复制了这个项目，你将会看到以下结构：

.. code-block:: bash

    invo/
        app/
            config/
            controllers/
            forms/
            library/
            logs/
            models/
            plugins/
            views/
        cache/
        docs/
        public/
            css/
            fonts/
            js/
        schemas/

正如你所知道的，Phalcon不会强求应用程序使用特定的文件结构。这个项目提供了一个简单的MVC模型和公共文档根目录。

一旦你打开浏览器输入 http://localhost/invo 浏览应用程序你将会看到下面这样：

.. raw:: html

    <img class="align-center" src="../static/img/invo-1.png">

这个应用分为两部分，一部分是前端，这个是一个公开的部分，浏览者可以接收关于INVO的信息，也可以请求联系人信息。第二部分是后端，一个管理员区域，一个注册用户可以管理他/她的产品和客户。

路由（Routing）
---------------
INVO使用内置的标准路由. :doc:`Router <routing>` 组件. 路由符合以下格式：`/:controller/:action/:params`. 这就意味着第一部分URI是控制器，第二部分是方法，剩余的是参数。

下面的路由 `/session/register` 执行的是 `SessionController` 控制器和它的 `registerAction` 方法。

配置（Configuration）
---------------------
INVO有一个设置应用常规参数的配置文件。这个文件位于 `app/config/config.ini`，并且他在应用引导文件的最开始就开始加载 (`public/index.php`)：

.. code-block:: php

    <?php

    use Phalcon\Config\Adapter\Ini as ConfigIni;

    // ...

    // Read the configuration
    $config = new ConfigIni(APP_PATH . 'app/config/config.ini');

:doc:`Phalcon\\Config <config>` 允许我们使用面向对象的方式来操作文件。在这个例子中，我们使用ini文件作为配置文件，然而，它对于配置文件有更多的适配支持。这个配置文件包含以下配置：

.. code-block:: ini

    [database]
    host     = localhost
    username = root
    password = secret
    name     = invo

    [application]
    controllersDir = app/controllers/
    modelsDir      = app/models/
    viewsDir       = app/views/
    pluginsDir     = app/plugins/
    formsDir       = app/forms/
    libraryDir     = app/library/
    baseUri        = /invo/

对于配置文件，Phalcon 没有任何提前预约好的惯例配置。通过节（Sections）帮助我们组织相应选项。在这个文件里 `application` 和 `database` 这两个部分将被用于后面的程序。

自动加载（Autoloaders）
-----------------------
在引导文件 (public/index.php) 的第二部分是自动加载器:

.. code-block:: php

    <?php

    /**
     * Auto-loader configuration
     */
    require APP_PATH . 'app/config/loader.php';

自动加载器注册一组目录列表，应用程序将根据需要从这组目录里查找需要的类文件。

.. code-block:: php

    <?php

    $loader = new Phalcon\Loader();

    // We're a registering a set of directories taken from the configuration file
    $loader->registerDirs(
        array(
            APP_PATH . $config->application->controllersDir,
            APP_PATH . $config->application->pluginsDir,
            APP_PATH . $config->application->libraryDir,
            APP_PATH . $config->application->modelsDir,
            APP_PATH . $config->application->formsDir,
        )
    )->register();

注意, 以上代码注册的目录是在配置文件中定义的. 唯一没有注册的目录是 `viewsDir`, 因为它包含 `HTML` + `PHP` 文件但不是类.
同时, 也要注意我们使用了常量 `APP_PATH`, 这个常量在引导文件 (public/index.php) 中被定义, 允许我们对我们项目的根路径有一个参考:

.. code-block:: php

    <?php

    // ...

    define('APP_PATH', realpath('..') . '/');

注册服务（Registering services）
--------------------------------
服务注册已经在前面的教程中实现了, 利用一个闭包来实现惰性加载组件：

.. code-block:: php

    <?php

    use Phalcon\Mvc\Url as UrlProvider;

    // ...

    /**
     * The URL component is used to generate all kind of URLs in the application
     */
    $di->set('url', function () use ($config) {
        $url = new UrlProvider();

        $url->setBaseUri($config->application->baseUri);

        return $url;
    });

We will discuss this file in depth later.

处理请求（Handling the Request）
--------------------------------
如果我们忽略文件 (public/index.php) 的结束, 请求最终会被 :doc:`Phalcon\\Mvc\\Application <../api/Phalcon_Mvc_Application>` 处理, 它会初始化并执行所有必要条件，使应用程序运行：

.. code-block:: php

    <?php

    use Phalcon\Mvc\Application;

    // ...

    $app = new Application();

    echo $app->handle()->getContent();

依赖注入（Dependency Injection）
--------------------------------
Phalcon 是一个高度解耦的框架，所以我们一个组件来充当胶水来让每个组件都能正常工作。这个组件就是 :doc:`Phalcon\\Di <../api/Phalcon_Di>`。这是一个服务容器，可以执行依赖注入和服务定位，实例化应用所需要的所有组件。

在容器中有多种注册服务的方法。在INVO里, 大部分服务使用匿名函数或者闭包来进行注册的, 对象以惰性的方式被实例化，减少了应用程序所需要的资源。

例如，下面摘录了 Session 服务的注册。当应用程序需要访问 Session 数据的时候，匿名函数才会被调用：

.. code-block:: php

    <?php

    use Phalcon\Session\Adapter\Files as Session;

    // ...

    // Start the session the first time a component requests the session service
    $di->set('session', function () {
        $session = new Session();

        $session->start();

        return $session;
    });

这里，我们可以自由的更改适配器，执行额外的初始化或者其他操作。注意，这个服务器是使用 `session` 名字进行注册的。这是一个惯例，来允许框架在服务容器中识别正在活动的服务.

一个请求可以使用多个服务，单独注册每个服务可以说是一个繁重的任务。因此，框架提供了 :doc:`Phalcon\\Di <../api/Phalcon_Di>` 的一个变种，称作  :doc:`Phalcon\\Di\\FactoryDefault <../api/Phalcon_Di_FactoryDefault>`，其任务是注册所有 MVC 所需要的服务来提供一个全栈框架。

.. code-block:: php

    <?php

    use Phalcon\DI\FactoryDefault;

    // ...

    // The FactoryDefault Dependency Injector automatically registers the
    // right services providing a full-stack framework
    $di = new FactoryDefault();

它注册了大部分框架提供的标准服务和组件。如果我们需要重写某些已经定义的服务，我们仅仅需要重新定义它，就像上面的 "session" 和 "url"一样，这就是变量  :code:`$di` 存在的原因.

在下一章，我们将会看到如何在INVO中实施认证和授权。

.. _Github: https://github.com/dreamsxin/invo
.. _Bootstrap: http://getbootstrap.com/
