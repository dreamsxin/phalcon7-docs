Phalcon7 开发工具（Phalcon7 Developer Tools）
=============================================
Phalcon7 提供的这个开发工具主要是用来辅助开发，比如生成一些程序的基本框架，生成控制器、模型等。使用这个工具我们只需要一个简单的命令即可生成应用的基本框架。

.. highlights::

    **非常重要:** 要使用这个工具我们必须要安装 Phalcon7 扩展才行。

下载开发工具（Download）
------------------------
该开发辅助工具已经包含在了源码中 Github_ 。

Linux 系统下使用 Phalcon 开发工具（Phalcon Developer Tools on Linux）
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
为文件 `phalcon.php` 创建软链接：

.. code-block:: bash

    ln -s ~/cphalcon7/devtools/phalcon.php /usr/bin/phalcon

    chmod ugo+x /usr/bin/phalcon

就这么简单，你已经安装好开发工具了。

获取可用的命令（Getting Available Commands）
--------------------------------------------
我们可以在虚拟控制台上输入如下命令： :code:`phalcon commands`

.. code-block:: sh

   $ phalcon commands

   Phalcon DevTools (2.0.8)

   Available commands:
     commands         (alias of: list, enumerate)
     controller       (alias of: create-controller)
     model            (alias of: create-model)
     all-models       (alias of: create-all-models)
     project          (alias of: create-project)
     scaffold         (alias of: create-scaffold)
     migration        (alias of: create-migration)
     webtools         (alias of: create-webtools)

生成项目框架（Generating a Project Skeleton）
---------------------------------------------
我们可以使用Phalcon开发辅助工具生成预先定义的项目架构。 默认情况下，phalcon开发辅助工具会使用apache的mod_rewrite来生成程序的骨架. 要创建项目我们只需要在我们的
web服务器根目录下输入如下命令：

.. code-block:: sh

      $ pwd

      /Applications/MAMP/htdocs

      $ phalcon create-project store

执行命令后会生成如下的文档结构的项目：

.. raw:: html

    <img class="align-center" src="../static/img/tools-2.png">

我们可以在命令上加 *--help* 以显示帮助信息（下面的帮助中的中文是翻译时加上去的）：

.. code-block:: sh

    $ phalcon project --help

    Phalcon DevTools (2.0.8)

    Help:
      Creates a project 创建项目

    Usage:
      project [name] [type] [directory] [enable-webtools]

    Arguments: 参数
      help    Shows this help text 显示此帮助信息

    Example 例子
      phalcon project store simple

    Options: 选项
     --name               Name of the new project 新项目的名字
     --enable-webtools    Determines if webtools should be enabled [optional] 此选项决定了新的项目中是否使用webtools开发辅助组件
     --directory=s        Base path on which project will be created [optional] 在何外创建项目
     --type=s             Type of the application to be generated (cli, micro, simple, modules) 应用的种类（微型，简单，多模块，console等）
     --template-path=s    Specify a template path [optional] 指定模板路径
     --template-engine=s  Define the template engine, default php [optional] 指定模板引擎
     --use-config-ini     Use a ini file as configuration file [optional] 使用ini文件作为配置保存文件
     --trace              Shows the trace of the framework in case of exception. [optional] 出错时是否显示框架的trace信息
     --help               Shows this help 显示帮助

我们访问新生成项目的地址显示如下：

.. raw:: html

    <img class="align-center" src="../static/img/tools-6.png">

生成控制器（Generating Controllers）
------------------------------------
我们可以使用`phalcon create-controller --name test`或`phalcon controller --name test`来生成名为`test`的控制器。
当然要使用此命令当前的执行命令目录必须为已存在的phalcon项目内。

.. code-block:: sh

         $ phalcon create-controller --name test

上面的命令会生成如下代码：

.. code-block:: php

    <?php

    class TestController extends Phalcon\Mvc\Controller
    {
        public function indexAction()
        {

        }
    }

数据库配置（Preparing Database Settings）
-----------------------------------------
当我们使用phalcon的辅助开发工具生成项目时，则生成的配置信息会被放在 *app/config/config.ini* 文件内。我们必须要正确的配置连接信息才可生成模型或基本的CRUD操作。

可以在config.ini中进行修改配置信息：

.. code-block:: ini

    [database]
    adapter  = Mysql
    host     = "127.0.0.1"
    username = "root"
    password = "secret"
    dbname   = "store_db"

    [phalcon]
    controllersDir = "../app/controllers/"
    modelsDir      = "../app/models/"
    viewsDir       = "../app/views/"
    baseUri        = "/store/"

生成模型（Generating Models）
-----------------------------
使用phalcon开发辅助工具我们可以有若干种方式来生成模型。 我人可以有选择的生成若干个模型或是全部生成。 亦可以指定生成公有属性或是生成setter和getter方法。

Options:
 --name=s             Table name 表名
 --schema=s           Name of the schema. [optional] schema名
 --namespace=s        Model's namespace [optional] 模型命名空间
 --get-set            Attributes will be protected and have setters/getters. [optional] 设置字段访问属性为私有 并添加setters/getters方法
 --extends=s          Model extends the class name supplied [optional] 指定扩展类名
 --excludefields=l    Excludes fields defined in a comma separated list [optional]
 --doc                Helps to improve code completion on IDEs [optional] 辅助IDE的自动完成功能
 --directory=s        Base path on which project will be created [optional] 项目的根目录
 --force              Rewrite the model. [optional] 重写模型
 --trace              Shows the trace of the framework in case of exception. [optional] 出错时显示框架trace信息
 --mapcolumn          Get some code for map columns. [optional] 生成字映射的代码
 --abstract           Abstract Model [optional]

最简单的生成模型的方式：

.. code-block:: sh

         $ phalcon model products

.. code-block:: sh

         $ phalcon model --name tablename

所有的字段设置为公有：

.. code-block:: php

    <?php

    class Products extends \Phalcon\Mvc\Model
    {
        /**
         * @var integer
         */
        public $id;

        /**
         * @var integer
         */
        public $types_id;

        /**
         * @var string
         */
        public $name;

        /**
         * @var string
         */
        public $price;

        /**
         * @var integer
         */
        public $quantity;

        /**
         * @var string
         */
        public $status;
    }

我们可以在生成模型时指定 *--get-set* 参数以实现对字面的保护， 这样我们可以在setter/getter方法里执行一些业务逻辑。

.. code-block:: php

    <?php

    class Products extends \Phalcon\Mvc\Model
    {
        /**
         * @var integer
         */
        protected $id;

        /**
         * @var integer
         */
        protected $types_id;

        /**
         * @var string
         */
        protected $name;

        /**
         * @var string
         */
        protected $price;

        /**
         * @var integer
         */
        protected $quantity;

        /**
         * @var string
         */
        protected $status;


        /**
         * Method to set the value of field id
         * @param integer $id
         */
        public function setId($id)
        {
            $this->id = $id;
        }

        /**
         * Method to set the value of field types_id
         * @param integer $types_id
         */
        public function setTypesId($types_id)
        {
            $this->types_id = $types_id;
        }

        // ...

        /**
         * Returns the value of field status
         * @return string
         */
        public function getStatus()
        {
            return $this->status;
        }
    }

另一个非常好的特性即是在我们多次生成模型时，原有的对模型的更改依然会存在。

生成基本的 CRUD（Scaffold a CRUD）
--------------------------------------
使用phalcon开发辅助工具我们可以直接快速的生成一个模型的CRUD操作。 如果我们想快速的生成模型的CRUD操作只需要使用phalcon辅助开发工具的中scaffold命令即可。

代码生成后，你可以根据自己的需要修改生成的代码。很多开发者可能不会去使用这个功能，其实这东西有时不是太好用，很多时候开发者往往会手动的书写相关代码。使用scaffold产生的代码可以
帮助我们理解框架是如何工作的当然也可以帮助我们制作出快速原型来。 下面的截图展示了基于products表的scaffold:

.. code-block:: sh

         $ phalcon scaffold --table-name products

scaffold生成器会在相关的文件夹中生成若干个文档。 下面是所生成文件的概览：

+----------------------------------------+--------------------------------+
| 文件                                   | 作用                           |
+========================================+================================+
| app/controllers/ProductsController.php | Products控制器                 |
+----------------------------------------+--------------------------------+
| app/models/Products.php                | Products模型                   |
+----------------------------------------+--------------------------------+
| app/views/layout/products.phtml        | Products控制器布局             |
+----------------------------------------+--------------------------------+
| app/views/products/new.phtml           | View for the action "new"      |
+----------------------------------------+--------------------------------+
| app/views/products/edit.phtml          | View for the action "edit"     |
+----------------------------------------+--------------------------------+
| app/views/products/search.phtml        | View for the action "search"   |
+----------------------------------------+--------------------------------+

在生成的Products控制器中，我们可以看到一个搜索表单和一个生成新product的链接：

.. raw:: html

    <img class="align-center" src="../static/img/tools-10.png">

在创建页面我们可以生成经过验证的Products记录。 Phalcon会自动的验证数据库中的非空字段。

.. raw:: html

    <img class="align-center" src="../static/img/tools-11.png">

执行搜索后，分页组件会显示颁后的结果。我们在结果列表的前面放置Edit或Delete链接，以实现相应的操作。

.. raw:: html

    <img class="align-center" src="../static/img/tools-12.png">

集成工具到 PhpStorm（Integrating Tools with PhpStorm IDE）
----------------------------------------------------------
在 PHP IDE 中包含 `devtools\ide\1.1.0` 就能在 IDE 中实现 Phalcon7 相关类和方法的自动提示。

结束语（Conclusion）
--------------------
Phalcon开发辅助工具为我们提供了一种简易的产生应用代码的方法，这可以减少开发时间及潜在的错误。

.. _Github: https://github.com/dreamsxin/cphalcon7
.. _PhpStorm IDE: http://www.jetbrains.com/phpstorm/
