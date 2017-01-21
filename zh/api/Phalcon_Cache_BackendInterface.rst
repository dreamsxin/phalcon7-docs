Interface **Phalcon\\Cache\\BackendInterface**
==============================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/cache/backendinterface.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Phalcon\\Cache\\BackendInterface initializer


Methods
-------

abstract public *mixed*  **start** (*string* $keyName, [*long* $lifetime])

Starts a cache. The $keyname allows to identify the created fragment



abstract public  **stop** ([*boolean* $stopBuffer])

Stops the frontend without store any cached content



abstract public *mixed*  **getFrontend** ()

Returns front-end instance adapter related to the back-end



abstract public *array*  **getOptions** ()

Returns the backend options



abstract public *boolean*  **isFresh** ()

Checks whether the last cache is fresh or cached



abstract public *boolean*  **isStarted** ()

Checks whether the cache has starting buffering or not



abstract public *mixed*  **get** (*string* $keyName)

Returns a cached content



abstract public  **save** ([*string* $keyName], [*unknown* $value], [*long* $lifetime], [*boolean* $stopBuffer])

Stores cached content into the file backend and stops the frontend



abstract public *boolean*  **delete** (*string* $keyName)

Deletes a value from the cache by its key



abstract public *array*  **queryKeys** ([*string* $prefix])

Query the existing cached keys



abstract public *boolean*  **exists** (*string* $keyName)

Checks if cache exists and it hasn't expired



abstract public *boolean*  **flush** ()

Immediately invalidates all existing items.



