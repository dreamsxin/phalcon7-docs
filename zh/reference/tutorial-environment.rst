教程 8：运行环境（Tutorial 8: Environments）
============================================

在本章节中，我们将会说明如何让同一套代码在开发环境和生产环境使用不同的配置文件，以及调用不同类。

项目结构（Project Structure）
-----------------------------
下面是我们的项目结构：

.. code-block:: bash

    evn/
    app/
        config/
        config.php
        config.dev.php
        controllers/
        dev/
        models/
        dev/
        views/
        dev/
        public/
        index.php

可以看到，在这里控制器、模型和视图目录分别多了一个，我将利用自动加载器查找目录的优先顺序来实现不同环境调用不同类，以及利用视图类查找视图文件的先后顺序来实现渲染不同的视图文件。

引导文件（Bootstrap）
---------------------
下面是引导文件 `public/index.php` 的实现，在这里我们是通过域名的不同来区别开发或生产环境，你们也可以通过配置来设定环境变量：

.. code-block:: php

    <?php

    $config_basedir = __DIR__ . '/../apps/config/';
    Phalcon\Config\Adapter\Php::setBasePath($config_basedir);

    $config = new Phalcon\Config\Adapter\Php('config.php');

    $host = Phalcon\Arr::get($_SERVER, 'HTTP_HOST', 'localhost');

    // 如果域名中包含 dev，就认为是开发环境
    if (stripos($host, 'dev') !== FALSE) {
        $environment = 'dev';
    } else if (stripos($host, 'test') !== FALSE) {
        $environment = 'test';
    } else {
        $environment = 'prod';
    }
	
	if ($environment == 'dev') {
        $filename = 'config.dev.php';
        if (file_exists($config_basedir . $filename)) {
            $config->merge($config->load($filename));
        }
    }

    if ($environment == 'test') {
        $filename = 'config.test.php';
        if (file_exists($config_basedir . $filename)) {
            $config->merge($config->load($filename));
        }
    }

    $loader = new \Phalcon\Loader();

    if ($environment == 'dev') {
        $dirs = array(
            $config->controllersDir . 'dev/',
            $config->controllersDir,
            $config->modelsDir . 'dev/',
            $config->modelsDir,
        );
    } else {
        $dirs = array(
            $config->controllersDir,
            $config->modelsDir,
        );
    }

    $loader->registerDirs($dirs)->register();

    $di = new \Phalcon\DI\FactoryDefault();

    $di->set('view', function () use ($config, $environment) {
        $view = new \Phalcon\Mvc\View();
        if ($environment == 'dev') {
            $dirs = array(
                $config->viewsDir . 'dev/',
                $config->viewsDir,
            );
        } else {
            $dirs = $config->viewsDir;
        }

        $view->setBasePath($dirs);
        return $view;
    }, true);

    // 如果为生产环境，则设置 metadata 缓存
    if ($environment == 'prod') {
        $di->set('modelsMetadata', function() {
            $metaData = new \Phalcon\Mvc\Model\Metadata\Files(array(
                'metaDataDir' => __DIR__ . DIRECTORY_SEPARATOR . '../apps/cache/metadata/'
             ));
             return $metaData;
        }, true);
    }
