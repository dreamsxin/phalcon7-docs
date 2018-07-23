面向切面编程（Aspect Oriented Programming）
===========================================

:code:`Phalcon\Aop 是一个通用组件，以非侵入的方式将系统级的功能代码切入到目标类的指定方法、字段上。

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
