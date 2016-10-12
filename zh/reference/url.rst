生成 URL 和 路径（Generating URLs and Paths）
=============================================

在Phalcon应用程序中，使用 :doc:`Phalcon\\Mvc\\Url <../api/Phalcon_Mvc_Url>` 组件生成URL。它能够生成基于路由的独立的URL。

设置站点基地址（Setting a base URI）
------------------------------------
根据你的应用程序安装到主机文档目录的位置，你的应用程序URI可能会出现一个基础的URI。

例如，如果你的主机文档目录是 /var/www/htdocs，而你的应用程序安装到 /var/www/htdocs/invo，那么基础URI即为 /invo/.如果你使用虚拟主机的形式安装此应用，那么baseUri即为 /. 执行以下代码，你可以检测你的应用程序的baseUri.

.. code-block:: php

    <?php

    use Phalcon\Mvc\Url;

    $url = new Url();
    echo $url->getBaseUri();

默认情况下，Phalcon 会自动检测应用程序的baseUri.但如果你想提高应用程序性能的话，推荐手工设置：

.. code-block:: php

    <?php

    use Phalcon\Mvc\Url;

    $url = new Url();

    // Setting a relative base URI
    $url->setBaseUri('/invo/');

    // Setting a full domain as base URI
    $url->setBaseUri('//my.domain.com/');

    // Setting a full domain as base URI
    $url->setBaseUri('http://my.domain.com/my-app/');

通常情况下，此组件必须被注册到服务容器中，因此你可以直接这样设置它：

.. code-block:: php

    <?php

    use Phalcon\Mvc\Url;

    $di->set('url', function () {
        $url = new Url();
        $url->setBaseUri('/invo/');
        return $url;
    });

生成 URI（Generating URIs）
---------------------------
如果你使用的是 :doc:`Router <routing>` 的默认行为。你的应用程序会匹配路由模式 : /:controller/:action/:params. 因此，很容易通过"get"方法得到：

.. code-block:: php

    <?php echo $url->get("products/save"); ?>

请注意，预先设置baseUri并不是必须的。如果你已经通过设置路由命名，你可以很容易改变它。例如，你有以下途径：

.. code-block:: php

    <?php

    $route->add(
        "/blog/{year}/{month}/{title}",
        array(
            'controller' => 'posts',
            'action'     => 'show'
        )
    )->setName('show-post');

生成URL还可以通过以下方式：

.. code-block:: php

    <?php

    // This produces: /blog/2015/01/some-blog-post
    $url->get(
        array(
            'for'   => 'show-post',
            'year'  => 2015,
            'month' => '01',
            'title' => 'some-blog-post'
        )
    );

如果使用 :doc:`Phalcon\\Mvc\\Router\\Route <../api/Phalcon_Mvc_Router_Route>` 的方法 :code:`setUrlGenerator` 设置了 URL 生成器，这里将会调用设置的 URL 生成器生成 URL。

没有伪静态状态下的生成 URL（Producing URLs without mod_rewrite）
----------------------------------------------------------------
你还可以使用此组件在不使用重写规则的情况下创建URL：

.. code-block:: php

    <?php

    use Phalcon\Mvc\Url;

    $url = new Url();

    // Pass the URI in $_GET["_url"]
    $url->setBaseUri('/invo/index.php?_url=/');

    // This produce: /invo/index.php?_url=/products/save
    echo $url->get("products/save");

你也可以使用 :code:`$_SERVER["REQUEST_URI"]`:

.. code-block:: php

    <?php

    use Phalcon\Mvc\Url;

    $url = new Url();

    // Pass the URI in $_GET["_url"]
    $url->setBaseUri('/invo/index.php?_url=/');

    // Pass the URI using $_SERVER["REQUEST_URI"]
    $url->setBaseUri('/invo/index.php/');

在这种情况下，你必须手工处理路由中的URI：

.. code-block:: php

    <?php

    use Phalcon\Mvc\Router;

    $router = new Router();

    // ... Define routes

    $uri = str_replace($_SERVER["SCRIPT_NAME"], '', $_SERVER["REQUEST_URI"]);
    $router->handle($uri);

产生的路由看起来像这样：

.. code-block:: php

    <?php

    // This produce: /invo/index.php/products/save
    echo $url->get("products/save");

Volt 中生成 URL（Volt Producing URLs from Volt）
------------------------------------------------
The function "url" is available in volt to generate URLs using this component:

.. code-block:: html+jinja

    <a href="{{ url("posts/edit/1002") }}">Edit</a>

Generate static routes:

.. code-block:: html+jinja

    <link rel="stylesheet" href="{{ static_url("css/style.css") }}" type="text/css" />

静态 URI 与 动态 URI（Static vs. Dynamic URIs）
-----------------------------------------------
This component allow you to set up a different base URI for static resources in the application:

.. code-block:: php

    <?php

    use Phalcon\Mvc\Url;

    $url = new Url();

    // Dynamic URIs are
    $url->setBaseUri('/');

    // Static resources go through a CDN
    $url->setStaticBaseUri('http://static.mywebsite.com/');

:doc:`Phalcon\\Tag <tags>` will request both dynamical and static URIs using this component.

自定义 URL 生成器（Implementing your own URL Generator）
--------------------------------------------------------
The :doc:`Phalcon\\Mvc\\UrlInterface <../api/Phalcon_Mvc_UrlInterface>` interface must be implemented to create your own URL
generator replacing the one provided by Phalcon.
