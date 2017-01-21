Class **Phalcon\\Cache\\SHMemory**
==================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/cache/shmemory.c" class="btn btn-default btn-sm">Source on GitHub</a>`

It can be used to replace APC or local memcached.


Methods
-------

public  **__construct** ([*string* $prefix])

Phalcon\\Cache\\SHMemory constructor



public :doc:`Phalcon\\Cache\\SHMemory <Phalcon_Cache_SHMemory>`  **set** (*string|array* $keys, [*mixed* $value], [*long* $lifetime])

Stores cached content



public *mixed*  **get** (*string|array* $keys)

Returns a cached content



public *boolean*  **delete** (*string|array* $keys, [*long* $lifetime])

Returns a cached content



public  **flush** ()

...


public  **dump** ([*unknown* $limit])

...


public  **__set** (*string* $key, *mixed* $value)

Stores cached content



public *mixed*  **__get** (*string* $key)

Returns a cached content



