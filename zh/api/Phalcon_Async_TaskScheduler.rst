Final class **Phalcon\\Async\\TaskScheduler**
=============================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/async/taskscheduler.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Methods
-------

private  **__construct** ()

...


public  **__wakeup** ()

...


public static  **run** (*unknown* $callback, [*unknown* $finalizer])

...


public static  **runWithContext** (:doc:`Phalcon\\Async\\Context <Phalcon_Async_Context>` $context, *unknown* $callback, [*unknown* $finalizer])

...


public static  **get** (*unknown* $type)

...


public static  **register** (*unknown* $type, *unknown* $factory)

...


public  **tick** (*unknown* $callback)

...


public  **timer** (*unknown* $callback)

...


public  **poll** (*unknown* $stream, *unknown* $callback)

...


