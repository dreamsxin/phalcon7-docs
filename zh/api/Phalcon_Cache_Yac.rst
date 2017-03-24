Class **Phalcon\\Cache\\Yac**
=============================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/cache/yac.c" class="btn btn-default btn-sm">Source on GitHub</a>`

It can be used to replace APC or local memcached.


Methods
-------

public  **__construct** ([*string* $prefix])

Phalcon\\Cache\\Yac constructor



public :doc:`Phalcon\\Cache\\Yac <Phalcon_Cache_Yac>`  **set** (*string|array* $keys, [*mixed* $value], [*long* $lifetime])

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



