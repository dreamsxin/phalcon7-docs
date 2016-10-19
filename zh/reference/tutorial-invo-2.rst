教程: 保护INVO（Tutorial: Securing INVO）
=============================================

In this chapter, we continue explaining how INVO is structured, we'll talk
about the implementation of authentication, authorization using events and plugins and
an access control list (ACL) managed by Phalcon.

登录应用（Log into the Application）
------------------------------------
一个 “登录” 功能将允许我们在后台控制器中工作。分离后台和前台的控制器是合理的。所有加载的控制器都位于相同的目录 (app/controllers/)。

为了进入系统，用户必须有一个有效的用户名和密码。用户存储在数据库 “invo” 里面的 “users” 表里面。

在我们开始会话之前，我们需要在数据库配置数据库的连接。注册一个 “db” 服务在服务容器中，并设置连接信息：

.. code-block:: php

    <?php

    use Phalcon\Db\Adapter\Pdo\Mysql as DbAdapter;

    // ...

    // Database connection is created based on parameters defined in the configuration file
    $di->set('db', function () use ($config) {
        return new DbAdapter(
            array(
                "host"     => $config->database->host,
                "username" => $config->database->username,
                "password" => $config->database->password,
                "dbname"   => $config->database->name
            )
        );
    });

这里，我们将会返回一个 MySQL 连接适配器的一个实例。如果需要，你可以做一些额外的操作比如添加一个日志记录，一个分析器或者更换成其他数据库适配器，设置你想要的。

下面是一个登录信息的表单 (app/views/session/index.phtml) 。我们已经删除了一些 HTML 代码来让例子更加简洁:

.. code-block:: html+jinja

    <?php echo Phalcon\Tag::form("session/start"); ?>
        <fieldset>
            <div>
                <label for="email">Username/Email</label>
                <div>
                    <?php echo Phalcon\Tag::textField("email"); ?>
                </div>
            </div>
            <div>
                <label for="password">Password</label>
                <div>
                    <?php echo Phalcon\Tag::passwordField("password"); ?>
                </div>
            </div>
            <div>
		<?php echo Phalcon\Tag::submitButton("Login"); ?>
            </div>
        </fieldset>
    </form>

:code:`SessionController::startAction` 方法 (app/controllers/SessionController.php) 有验证表单中输入的数据包括检查在数据库中是否为有效用户的任务：

.. code-block:: php

    <?php

    class SessionController extends ControllerBase
    {
        // ...

        private function _registerSession($user)
        {
            $this->session->set(
                'auth',
                array(
                    'id'   => $user->id,
                    'name' => $user->name
                )
            );
        }

        /**
         * This action authenticate and logs a user into the application
         */
        public function startAction()
        {
            if ($this->request->isPost()) {

                // Get the data from the user
                $email    = $this->request->getPost('email');
                $password = $this->request->getPost('password');

                // Find the user in the database
                $user = Users::findFirst(
                    array(
                        "(email = :email: OR username = :email:) AND password = :password: AND active = 'Y'",
                        'bind' => array(
                            'email'    => $email,
                            'password' => sha1($password)
                        )
                    )
                );

                if ($user != false) {

                    $this->_registerSession($user);

                    $this->flash->success('Welcome ' . $user->name);

                    // Forward to the 'invoices' controller if the user is valid
                    return $this->dispatcher->forward(
                        array(
                            'controller' => 'invoices',
                            'action'     => 'index'
                        )
                    );
                }

                $this->flash->error('Wrong email/password');
            }

            // Forward to the login form again
            return $this->dispatcher->forward(
                array(
                    'controller' => 'session',
                    'action'     => 'index'
                )
            );
        }
    }

为简单起见，我们使用 "sha1_" 在数据库中存储密码散列，然而，在实际应用中不建议采用此算法，使用 ":doc:`bcrypt <security>`" 代替。

请注意，多个公共属性在控制器访问，像: :code:`$this->flash`，:code:`$this->request` 或者 :code:`$this->session`。这些是先前在服务容器中定义的服务 (app/config/services。php)。当它们第一次访问的时候，它们被注入作为控制器的一部分。

这些服务是"共享"的，这意味着我们总是访问相同的地方，无论我们在哪里调用它们。

例如，这里我们调用 "session" 服务然后我们在变量 "auth" 中存储用户身份：

.. code-block:: php

    <?php

    $this->session->set(
        'auth',
        array(
            'id'   => $user->id,
            'name' => $user->name
        )
    );

本节的另外一个重要方面是如何验证用户为有效的，首先我们验证是否是POST请求的：

.. code-block:: php

    <?php

    if ($this->request->isPost()) {

然后，我们接收表单中的参数：

.. code-block:: php

    <?php

    $email    = $this->request->getPost('email');
    $password = $this->request->getPost('password');

现在，我们需要检查是否存在一个相同的用户名或邮箱和密码的用户：

.. code-block:: php

    <?php

    $user = Users::findFirst(
        array(
            "(email = :email: OR username = :email:) AND password = :password: AND active = 'Y'",
            'bind' => array(
                'email'    => $email,
                'password' => sha1($password)
            )
        )
    );

如果用户是有效的，我们将会在session中注册它，并且转发到 dashboard：

.. code-block:: php

    <?php

    if ($user != false) {
        $this->_registerSession($user);
        $this->flash->success('Welcome ' . $user->name);

        return $this->forward('invoices/index');
    }

如果用户不存在，用户将返回登录表单页：

.. code-block:: php

    <?php

    return $this->forward('session/index');

后端安全（Securing the Backend）
--------------------------------
后端是一个私有区域，只有已经注册并登录的用户才可以访问。因此，只有登录用户才能访问控制器这样的检验是有必要的。如果你没有登录到应用中并试图访问，例如 products 控制器 (这是私有的) 你将会看到如下屏幕：

.. raw:: html

    <img class="align-center" src="../static/img/invo-2.png">

每次有人试图访问任何 `controller/action`，应用将会验证当前角色 (在session中) 是否能够访问它，否则就会显示一个像上面那样的消息并转发到首页。

Now let's find out how the application accomplishes this. The first thing to know is that
there is a component called :doc:`Dispatcher <dispatching>`. It is informed about the route
found by the :doc:`Routing <routing>` component. Then, it is responsible for loading the
appropriate controller and execute the corresponding action method.

Normally, the framework creates the Dispatcher automatically. In our case, we want to perform a verification
before executing the required action, checking if the user has access to it or not. To achieve this, we have
replaced the component by creating a function in the bootstrap:

.. code-block:: php

    <?php

    use Phalcon\Mvc\Dispatcher;

    // ...

    /**
     * MVC dispatcher
     */
    $di->set('dispatcher', function () {

        // ...

        $dispatcher = new Dispatcher();

        return $dispatcher;
    });

We now have total control over the Dispatcher used in the application. Many components in the framework trigger
events that allow us to modify their internal flow of operation. As the Dependency Injector component acts as glue
for components, a new component called :doc:`EventsManager <events>` allows us to intercept the events produced
by a component, routing the events to listeners.

事件管理（Events Management）
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
An :doc:`EventsManager <events>` allows us to attach listeners to a particular type of event. The type that
interests us now is "dispatch". The following code filters all events produced by the Dispatcher:

.. code-block:: php

    <?php

    use Phalcon\Mvc\Dispatcher;
    use Phalcon\Events\Manager as EventsManager;

    $di->set('dispatcher', function () {

        // Create an events manager
        $eventsManager = new EventsManager();

        // Listen for events produced in the dispatcher using the Security plugin
        $eventsManager->attach('dispatch:beforeExecuteRoute', new SecurityPlugin);

        // Handle exceptions and not-found exceptions using NotFoundPlugin
        $eventsManager->attach('dispatch:beforeException', new NotFoundPlugin);

        $dispatcher = new Dispatcher();

        // Assign the events manager to the dispatcher
        $dispatcher->setEventsManager($eventsManager);

        return $dispatcher;
    });

When an event called "beforeExecuteRoute" is triggered the following plugin will be notified:

.. code-block:: php

    <?php

    /**
     * Check if the user is allowed to access certain action using the SecurityPlugin
     */
    $eventsManager->attach('dispatch:beforeExecuteRoute', new SecurityPlugin);

When a "beforeException" is triggered then other plugin is notified:

.. code-block:: php

    <?php

    /**
     * Handle exceptions and not-found exceptions using NotFoundPlugin
     */
    $eventsManager->attach('dispatch:beforeException', new NotFoundPlugin);

SecurityPlugin is a class located at (app/plugins/SecurityPlugin.php). This class implements the method
"beforeExecuteRoute". This is the same name as one of the events produced in the Dispatcher:

.. code-block:: php

    <?php

    use Phalcon\Events\Event;
    use Phalcon\Mvc\User\Plugin;
    use Phalcon\Mvc\Dispatcher;

    class SecurityPlugin extends Plugin
    {
        // ...

        public function beforeExecuteRoute(Event $event, Dispatcher $dispatcher)
        {
            // ...
        }
    }

The hook events always receive a first parameter that contains contextual information of the event produced (:code:`$event`)
and a second one that is the object that produced the event itself (:code:`$dispatcher`). It is not mandatory that
plugins extend the class :doc:`Phalcon\\Mvc\\User\\Plugin <../api/Phalcon_Mvc_User_Plugin>`, but by doing this they gain easier access to the services
available in the application.

Now, we're verifying the role in the current session, checking if the user has access using the ACL list.
If the user does not have access we redirect to the home screen as explained before:

.. code-block:: php

    <?php

    use Phalcon\Acl;
    use Phalcon\Events\Event;
    use Phalcon\Mvc\User\Plugin;
    use Phalcon\Mvc\Dispatcher;

    class SecurityPlugin extends Plugin
    {
        // ...

        public function beforeExecuteRoute(Event $event, Dispatcher $dispatcher)
        {
            // Check whether the "auth" variable exists in session to define the active role
            $auth = $this->session->get('auth');
            if (!$auth) {
                $role = 'Guests';
            } else {
                $role = 'Users';
            }

            // Take the active controller/action from the dispatcher
            $controller = $dispatcher->getControllerName();
            $action = $dispatcher->getActionName();

            // Obtain the ACL list
            $acl = $this->getAcl();

            // Check if the Role have access to the controller (resource)
            $allowed = $acl->isAllowed($role, $controller, $action);
            if ($allowed != Acl::ALLOW) {

                // If he doesn't have access forward him to the index controller
                $this->flash->error("You don't have access to this module");
                $dispatcher->forward(
                    array(
                        'controller' => 'index',
                        'action'     => 'index'
                    )
                );

                // Returning "false" we tell to the dispatcher to stop the current operation
                return false;
            }
        }
    }

提供 ACL 列表（Providing an ACL list）
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
In the above example we have obtained the ACL using the method :code:`$this->getAcl()`. This method is also
implemented in the Plugin. Now we are going to explain step-by-step how we built the access control list (ACL):

.. code-block:: php

    <?php

    use Phalcon\Acl;
    use Phalcon\Acl\Role;
    use Phalcon\Acl\Adapter\Memory as AclList;

    // Create the ACL
    $acl = new AclList();

    // The default action is DENY access
    $acl->setDefaultAction(Acl::DENY);

    // Register two roles, Users is registered users
    // and guests are users without a defined identity
    $roles = array(
        'users'  => new Role('Users'),
        'guests' => new Role('Guests')
    );

    foreach ($roles as $role) {
        $acl->addRole($role);
    }

Now, we define the resources for each area respectively. Controller names are resources and their actions are
accesses for the resources:

.. code-block:: php

    <?php

    use Phalcon\Acl\Resource;

    // ...

    // Private area resources (backend)
    $privateResources = array(
      'companies'    => array('index', 'search', 'new', 'edit', 'save', 'create', 'delete'),
      'products'     => array('index', 'search', 'new', 'edit', 'save', 'create', 'delete'),
      'producttypes' => array('index', 'search', 'new', 'edit', 'save', 'create', 'delete'),
      'invoices'     => array('index', 'profile')
    );
    foreach ($privateResources as $resource => $actions) {
        $acl->addResource(new Resource($resource), $actions);
    }

    // Public area resources (frontend)
    $publicResources = array(
        'index'    => array('index'),
        'about'    => array('index'),
        'register' => array('index'),
        'errors'   => array('show404', 'show500'),
        'session'  => array('index', 'register', 'start', 'end'),
        'contact'  => array('index', 'send')
    );
    foreach ($publicResources as $resource => $actions) {
        $acl->addResource(new Resource($resource), $actions);
    }

The ACL now have knowledge of the existing controllers and their related actions. Role "Users" has access to
all the resources of both frontend and backend. The role "Guests" only has access to the public area:

.. code-block:: php

    <?php

    // Grant access to public areas to both users and guests
    foreach ($roles as $role) {
        foreach ($publicResources as $resource => $actions) {
            $acl->allow($role->getName(), $resource, '*');
        }
    }

    // Grant access to private area only to role Users
    foreach ($privateResources as $resource => $actions) {
        foreach ($actions as $action) {
            $acl->allow('Users', $resource, $action);
        }
    }

Hooray!, the ACL is now complete. In next chapter, we will see how a CRUD is implemented in Phalcon and how you
can customize it.

.. _sha1: http://php.net/manual/zh/function.sha1.php
