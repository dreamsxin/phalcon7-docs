Final class **Phalcon\\Async\\Deferred**
========================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/async/deferred.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Methods
-------

public  **__construct** ([*unknown* $cancel])

...


public  **__debugInfo** ()

...


public  **awaitable** ()

...


public  **resolve** ([*unknown* $value])

...


public  **fail** ([*Throwable* $error])

...


public static  **value** ([*unknown* $value])

...


public static  **error** (*Throwable* $error)

...


public static  **combine** (*array* $awaitables, *unknown* $continuation)

...


public static  **transform** (:doc:`Phalcon\\Async\\Awaitable <Phalcon_Async_Awaitable>` $awaitable, *unknown* $continuation)

...


