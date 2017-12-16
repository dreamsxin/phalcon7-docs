Class **Phalcon\\Sync\\Sharedmemory**
=====================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/sync/sharedmemory.c" class="btn btn-default btn-sm">Source on GitHub</a>`




Methods
-------

public  **__construct** (*string* $name, *int* $size)

Phalcon\\Sync\\Sharedmemory constructor



public *boolean*  **first** ()

Returns whether or not this shared memory segment is the first time accessed (i.e. not initialized)



public  **size** ()

...


public *string*  **read** ([*int* $start], [*int* $length])

Copies data from shared memory



public *int*  **write** (*unknown* $string, [*int* $start])

Copies data to shared memory



