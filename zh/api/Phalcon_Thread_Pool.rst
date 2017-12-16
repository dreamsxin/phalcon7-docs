Class **Phalcon\\Thread\\Pool**
===============================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/thread/pool.c" class="btn btn-default btn-sm">Source on GitHub</a>`


.. code-block:: php

    <?php

     $pool = new Phalcon\Thread\Pool(2);
     $pool->add(function(){ echo 'Hello world!';});



Methods
-------

public  **__construct** ([*int* $num])

Phalcon\\Thread\\Pool constructor



public *int*  **getNumThreads** ()





public *boolean*  **inc** (*int* $num)





public *boolean*  **dec** (*int* $num)





public  **add** (*unknown* $work, [*array* $args])





public  **wait** ()





public  **destroy** ()





