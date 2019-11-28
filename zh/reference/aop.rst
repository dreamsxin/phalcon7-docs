AOP面向切面编程（Aspect Oriented Programming）
==============================================

:doc:`Phalcon\\Aop <../api/Phalcon_Aop>` 是一个通用组件，以非侵入的方式将系统级的功能代码切入到目标类的指定方法、成员变量上。

.. code-block:: php

    <?php

     class MyServices {
        private $val = 0;
        public function doVal() {
            echo 'Myval='.$this->val.PHP_EOL;
            $this->val++;
            echo 'Myval='.$this->val.PHP_EOL;
        }
    }

    $pointcut = 'MyServices::doVal()';
    $advice = function($joinpoint){
        echo $joinpoint->getProperty('val').'='.$$joinpoint->setProperty('val', 3).PHP_EOL;
    };
    Phalcon\Aop::addBefore($pointcut, $advice);

    $services = new MyServices();
    $services->doVal();

在上面的例子中，我们在 `doVal` 方法调用前修改了 `val` 的值。

可以把对成员变量的访问和更新作为通知的连接点（该功能在 PHP >= 7.4 版本中弃用）：

.. code-block:: php

    <?php

     class MyServices {
        private $val = 0;
        public function doVal() {
            echo 'Myval='.$this->val.PHP_EOL;
            $this->val++;
            echo 'Myval='.$this->val.PHP_EOL;
        }
    }

    $pointcut = 'read MyServices->val';
    $advice = function($joinpoint){
        echo $joinpoint->getPropertyName().'='.$$joinpoint->setPropertyValue().PHP_EOL;
    };
    Phalcon\Aop::addBefore($pointcut, $advice);

    $pointcut = 'write MyServices->val';
    $advice = function($joinpoint){
        $joinpoint->setAssignedValue(2);
    };
    Phalcon\Aop::addBefore($pointcut, $advice);

    $services = new MyServices();
    $services->doVal();

使用 AOP 实现业务层读写分离
---------------------------
该功能通过将对方法 :code:`Phalcon\Mvc\Model\Query::getConnection()` 的访问作为连接点来实现：

.. code-block:: php

    <?php

    $pointcut = 'Phalcon\Mvc\Model\Query::getConnection()';
    $advice = function($joinpoint){
        // 通过参数来选择
        $args = $joinpoint->getArguments();
        // 通过 SQL 类型来选择
        $query = $joinpoint->getObject();
        $query->getType(); // Phalcon\Mvc\Model\Query::TYPE_SELECT
        // ...
	return $db;
    };
    Phalcon\Aop::addAfter($pointcut, $advice);

或者通过将对方法 :code:`Phalcon\Mvc\Model\Query::getReadConnection()` 和 :code:`Phalcon\Mvc\Model\Query::getWriteConnection()` 的访问作为连接点来实现。