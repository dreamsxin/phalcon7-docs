用户组件类（User Component Class）
==================================
Phalcon 提供许多类来简化常见编码，如对文本或数组的操作， HTML 标签生成等等。

组件类一览（Overview）
----------------------

组件类列表（Component Class List）
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

+---------------+-------------------------------------------------------------------------------+
| 名称          | 描述                                                                          |
+===============+===============================================================================+
| 插件类        | :doc:`Phalcon\\Mvc\\User\\Plugin <../api/Phalcon_Mvc_User_Plugin>`            |
+---------------+-------------------------------------------------------------------------------+
| 组件类        | :doc:`Phalcon\\Mvc\\User\\Component <../api/Phalcon_Mvc_User_Component>`      |
+---------------+-------------------------------------------------------------------------------+
| 模块类        | :doc:`Phalcon\\Mvc\\User\\Module <../api/Phalcon_Mvc_User_Module>`            |
+---------------+-------------------------------------------------------------------------------+
| 逻辑类        | :doc:`Phalcon\\Mvc\\User\\Logic <../api/Phalcon_Mvc_User_Logic>`              |
+---------------+-------------------------------------------------------------------------------+
| 逻辑模型类    | :doc:`Phalcon\\Mvc\\User\\Logic\\Model <../api/Phalcon_Mvc_User_Logic_Model>` |
+---------------+-------------------------------------------------------------------------------+

插件类（Plugin Class）
----------------------
一般用于事件的拦截处理，例如权限检测插件 `SecurityPlugin`：

.. code-block:: php

    <?php

    use Phalcon\Acl;
    use Phalcon\Events\Event;
    use Phalcon\Mvc\User\Plugin;

    class SecurityPlugin extends Plugin
    {
        public function isAllowed($role, $controller, $action)
	{
            // ...
	}

        public function beforeExecuteRoute(Phalcon\Events\Event $event, Phalcon\Mvc\Dispatcher $dispatcher)
        {
            $auth = $this->session->get('auth');
            if (!$auth) {
                $role = 'Guests';
            } else {
                $role = 'Users';
            }

            $controller = $dispatcher->getControllerName();
            $action = $dispatcher->getActionName();

            $allowed = $this->isAllowed($role, $controller, $action);
            if ($allowed != Acl::ALLOW) {

                $this->flash->error("You don't have access to this module");
                $dispatcher->forward(
                    array(
                        'controller' => 'index',
                        'action'     => 'index'
                    )
                );

                return false;
            }
        }
    }

.. code-block:: php

    <?php

    $di->set('dispatcher', function () {
        $eventsManager = new EventsManager();
        $eventsManager->attach('dispatch:beforeExecuteRoute', new SecurityPlugin);

        $dispatcher = new Dispatcher();
        $dispatcher->setEventsManager($eventsManager);
        return $dispatcher;
    });

组件类（Component Class）
-------------------------
一般用于对框架功能的扩展。

模块类（Module Class）
----------------------
一般用于对框架功能的扩展。

逻辑类（Logic Class）
---------------------
一般用于处理业务逻辑，可以设置调度器绑定逻辑类，会根据控制器方法参数自动调用逻辑类静态方法 `call` 完成实例化，然后调用 `start` 完成初始化操作，
当控制器方法执行结束后，将调用 `finish` 方法：

.. code-block:: php

    <?php

    $di->set('dispatcher', function () {
        $dispatcher = new Dispatcher();
        $dispatcher->setLogicBinding(true);
        return $dispatcher;
    });

控制器实现：

.. code-block:: php

    <?php

    class LogicController extends Phalcon\Mvc\Controller
    {
        public function indexAction(\MyLogic $logic)
        {
	    // ...
        }
    }

逻辑类实现：

.. code-block:: php

    <?php

    class MyLogic extends Phalcon\Mvc\User\Logic
    {
        public $num = 0;

	public function start()
	{
            // ...
        }

	public function finish()
	{
            // ...
	    $this->view->data = $this->getContent();
        }

	// 该方法可以不实现
	public static function call($action = NULL, $params = NULL)
	{
            $logic = new MyLogic($action, $params);
            $logic->num = 1;
            return $logic;
        }
    }

逻辑模型类（Logic Model Class）
-------------------------------
使用方法与逻辑类相同，比逻辑类多了抽象方法`get`、`getAll`、`save`、`create`、`delete`、`deleteAll`、`update`、`updateAll`、`count`。

.. code-block:: php

    class Mylogic extends Phalcon\Mvc\User\Logic\Model {
        public function get($arguments = NULL){}
        public function getAll($arguments = NULL){}
        public function save($arguments = NULL){}
        public function create($arguments = NULL){}
        public function delete($arguments = NULL){}
        public function deleteAll($arguments = NULL){}
        public function update($arguments = NULL){}
        public function updateAll($arguments = NULL){}
        public function count($arguments = NULL){}
    }
