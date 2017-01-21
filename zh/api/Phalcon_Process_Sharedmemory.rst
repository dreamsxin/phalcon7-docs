Class **Phalcon\\Process\\Sharedmemory**
========================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/process/sharedmemory.c" class="btn btn-default btn-sm">Source on GitHub</a>`

This class defines sharedmemory entity and its description


Methods
-------

final public  **__construct** (*unknown* $name)

Phalcon\\Process\\Sharedmemory constructor



public  **isOpen** ()

Checks if open a shared memory file



public  **getName** ()

Gets the name



public  **getSize** ()

Gets the size



public  **open** ()

Open a shared memory



public  **create** (*unknown* $size)

Create a shared memory



public  **lock** ([*unknown* $blocking])

Lock the shared memory



public  **unlock** ([*unknown* $force])

Unock the shared memory



public  **read** ()

Read the shared memory



public  **write** (*unknown* $value)

Write the shared memory



