Class **Phalcon\\Aop**
======================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/aop.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Phalcon\\Arr  Provides utilities to work with arrs


Constants
---------

*integer* **KIND_BEFORE**

*integer* **KIND_AFTER**

*integer* **KIND_AROUND**

*integer* **KIND_PROPERTY**

*integer* **KIND_FUNCTION**

*integer* **KIND_METHOD**

*integer* **KIND_READ**

*integer* **KIND_WRITE**

*integer* **KIND_AROUND_WRITE_PROPERTY**

*integer* **KIND_AROUND_READ_PROPERTY**

*integer* **KIND_BEFORE_WRITE_PROPERTY**

*integer* **KIND_BEFORE_READ_PROPERTY**

*integer* **KIND_AFTER_WRITE_PROPERTY**

*integer* **KIND_AFTER_READ_PROPERTY**

*integer* **KIND_BEFORE_METHOD**

*integer* **KIND_AFTER_METHOD**

*integer* **KIND_AROUND_METHOD**

*integer* **KIND_BEFORE_FUNCTION**

*integer* **KIND_AFTER_FUNCTION**

*integer* **KIND_AROUND_FUNCTION**

Methods
-------

public static  **addBefore** (*unknown* $pointcut, *unknown* $advice)

Adds an advice to be run before the matching join points 

.. code-block:: php

    <?php

    \Phalcon\Aop::addBefore('mytest::test()', function(Phalcon\Aop\Joinpoint $obj){
    	echo "before";
    })




public static  **addAfter** (*unknown* $pointcut, *unknown* $advice)

Adds an advice to be run after the matching join points 

.. code-block:: php

    <?php

    \Phalcon\Aop::addAfter('mytest::test()', function(Phalcon\Aop\Joinpoint $obj){
    	echo "after";
    })




public static  **addAfterReturning** (*unknown* $pointcut, *unknown* $advice)

Links advices that becomes active after the target normally returns from execution (no exception). 

.. code-block:: php

    <?php

    \Phalcon\Aop::addAfterReturning('mytest::test()', function(Phalcon\Aop\Joinpoint $obj){
    	if ($obj->getReturnedValue() === null) {
    		echo "I'm updating {$obj->getMethodName()} in {$obj->getClassName()}, now returning this";
    		$obj->setReturnedValue($obj->getObject());
    	}
    })




public static  **addAfterThrowing** (*unknown* $pointcut, *unknown* $advice)

Links advices that becomes active if the target raise an (uncaught) exception.



public static  **addAround** (*unknown* $pointcut, *unknown* $advice)

Adds an advice to be run around the matching join points 

.. code-block:: php

    <?php

    \Phalcon\Aop::addAround('mytest::test()', function(Phalcon\Aop\Joinpoint $obj){
    	return $obj->process();
    })




