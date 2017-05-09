自动加载器（Universal Class Loader）
====================================
:doc:`Phalcon\\Loader <../api/Phalcon_Loader>` 组件允许你定义类的自动加载则规。

该组件基于 PHP 的 `spl_autoload_register` 函数实现尚未被定义的类（class）和接口（interface）的自动加载 `autoloading classes`_。
利用该组件实现 `lazy initialization`_。我们可以从其他项目或者第三方库加载文件，
兼容 `PSR-0 <https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-0.md>`_ and `PSR-4 <https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-4.md>`_ 标准.

:doc:`Phalcon\\Loader <../api/Phalcon_Loader>` 提供了 4 种加载方式，可以组合使用它们。

注册命名空间（Registering Namespaces）
--------------------------------------
当我们使用命名空间组织代码或者使用带有命名空间的外部库时，可以使用 `registerNamespaces` 提供的加载机制。
它的值是一个关联数组，键对应命名空间前缀，值是对应的目录。
当加载程序试图通过命名空间找到类时，命名空间的分隔符将被目录分隔符替换，然后作为查找的文件路径。

.. code-block:: php

    <?php

    use Phalcon\Loader;

    // Creates the autoloader
    $loader = new Loader();

    // Register some namespaces
    $loader->registerNamespaces(
        array(
           "Example\Base"    => "vendor/example/base/",
           "Example\Adapter" => "vendor/example/adapter/",
           "Example"         => "vendor/example/"
        )
    );

    // Register autoloader
    $loader->register();

    // The required class will automatically include the
    // file vendor/example/adapter/Some.php
    $some = new Example\Adapter\Some();

注册前缀（Registering Prefixes）
--------------------------------
这个策略类似于命名空间策略。它需要一个关联数组，其中键是前缀，它们的值是类所在的目录。
当加载程序试图通过命名空间找到类时，命名空间的分隔符和下划线 “_” 将被目录分隔符替换。

.. code-block:: php

    <?php

    use Phalcon\Loader;

    // Creates the autoloader
    $loader = new Loader();

    // Register some prefixes
    $loader->registerPrefixes(
        array(
            "Example_Base"    => "vendor/example/base/",
            "Example_Adapter" => "vendor/example/adapter/",
            "Example_"        => "vendor/example/"
        )
    );

    // Register autoloader
    $loader->register();

    // The required class will automatically include the
    // file vendor/example/adapter/Some.php
    $some = new Example_Adapter_Some();

注册文件夹（Registering Directories）
-------------------------------------
在文件目录多时不推荐该方法，它按照目录在数组内的顺序从上到下，查找文件。

.. code-block:: php

    <?php

    use Phalcon\Loader;

    // Creates the autoloader
    $loader = new Loader();

    // Register some directories
    $loader->registerDirs(
        array(
            "library/MyComponent/",
            "library/OtherComponent/Other/",
            "vendor/example/adapters/",
            "vendor/example/"
        )
    );

    // Register autoloader
    $loader->register();

    // The required class will automatically include the file from
    // the first directory where it has been located
    // i.e. library/OtherComponent/Other/Some.php
    $some = new Some();

注册类名（Registering Classes）
-------------------------------
最后一个方式，是直接将类名和文件对应起来，这是性能最好的加载方式，但类的列表不太好维护，所以不推荐使用。

.. code-block:: php

    <?php

    use Phalcon\Loader;

    // Creates the autoloader
    $loader = new Loader();

    // Register some classes
    $loader->registerClasses(
        array(
            "Some"         => "library/OtherComponent/Other/Some.php",
            "Example\Base" => "vendor/example/adapters/Example/BaseClass.php"
        )
    );

    // Register autoloader
    $loader->register();

    // Requiring a class will automatically include the file it references
    // in the associative array
    // i.e. library/OtherComponent/Other/Some.php
    $some = new Some();

额外的扩展名（Additional file extensions）
------------------------------------------
Some autoloading strategies such as  "prefixes", "namespaces" or "directories" automatically append the "php" extension at the end of the checked file. If you
are using additional extensions you could set it with the method "setExtensions". Files are checked in the order as it were defined:

.. code-block:: php

    <?php

    // Creates the autoloader
    $loader = new \Phalcon\Loader();

    // Set file extensions to check
    $loader->setExtensions(array("php", "inc", "phb"));

修改当前策略（Modifying current strategies）
--------------------------------------------
Additional auto-loading data can be added to existing values in the following way:

.. code-block:: php

    <?php

    // Adding more directories
    $loader->registerDirs(
        array(
            "../app/library/",
            "../app/plugins/"
        ),
        true
    );

Passing "true" as second parameter will merge the current values with new ones in any strategy.

安全层（Security Layer）
------------------------
:doc:`Phalcon\\Loader <../api/Phalcon_Loader>` offers a security layer sanitizing by default class names avoiding possible inclusion of unauthorized files.
Consider the following example:

.. code-block:: php

    <?php

    // Basic autoloader
    spl_autoload_register(function ($className) {
        if (file_exists($className . '.php')) {
            require $className . '.php';
        }
    });

The above auto-loader lacks of any security check, if by mistake in a function that launch the auto-loader,
a malicious prepared string is used as parameter this would allow to execute any file accessible by the application:

.. code-block:: php

    <?php

    // This variable is not filtered and comes from an insecure source
    $className = '../processes/important-process';

    // Check if the class exists triggering the auto-loader
    if (class_exists($className)) {
        // ...
    }

If '../processes/important-process.php' is a valid file, an external user could execute the file without
authorization.

To avoid these or most sophisticated attacks, :doc:`Phalcon\\Loader <../api/Phalcon_Loader>` removes any invalid character from the class name
reducing the possibility of being attacked.

自动加载事件（Autoloading Events）
----------------------------------
In the following example, the EventsManager is working with the class loader, allowing us to obtain debugging information regarding the flow of operation:

.. code-block:: php

    <?php

    $eventsManager = new \Phalcon\Events\Manager();

    $loader = new \Phalcon\Loader();

    $loader->registerNamespaces(
        array(
            'Example\\Base'    => 'vendor/example/base/',
            'Example\\Adapter' => 'vendor/example/adapter/',
            'Example'          => 'vendor/example/'
        )
    );

    // Listen all the loader events
    $eventsManager->attach('loader', function ($event, $loader) {
        if ($event->getType() == 'beforeCheckPath') {
            echo $loader->getCheckedPath();
        }
    });

    $loader->setEventsManager($eventsManager);

    $loader->register();

Some events when returning boolean false could stop the active operation. The following events are supported:

+------------------+---------------------------------------------------------------------------------------------------------------------+---------------------+
| Event Name       | Triggered                                                                                                           | Can stop operation? |
+==================+=====================================================================================================================+=====================+
| beforeCheckClass | Triggered before starting the autoloading process                                                                   | Yes                 |
+------------------+---------------------------------------------------------------------------------------------------------------------+---------------------+
| pathFound        | Triggered when the loader locate a class                                                                            | No                  |
+------------------+---------------------------------------------------------------------------------------------------------------------+---------------------+
| afterCheckClass  | Triggered after finish the autoloading process. If this event is launched the autoloader didn't find the class file | No                  |
+------------------+-----------------------------------------------------------+---------------------------------------------------------+---------------------+

注意事项（Troubleshooting）
---------------------------
Some things to keep in mind when using the universal autoloader:

* Auto-loading process is case-sensitive, the class will be loaded as it is written in the code
* Strategies based on namespaces/prefixes are faster than the directories strategy
* If a cache bytecode like APC_ is installed this will used to retrieve the requested file (an implicit caching of the file is performed)

.. _autoloading classes: http://www.php.net/manual/en/language.oop5.autoload.php
.. _lazy initialization: http://en.wikipedia.org/wiki/Lazy_initialization
.. _APC: http://php.net/manual/en/book.apc.php
