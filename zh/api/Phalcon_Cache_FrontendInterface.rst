Interface **Phalcon\\Cache\\FrontendInterface**
===============================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/phalcon/cache/frontendinterface.zep" class="btn btn-default btn-sm">Source on GitHub</a>`

Phalcon\\Cache\\FrontendInterface initializer


Methods
-------

abstract public *int*  **getLifetime** ()

Returns the cache lifetime



abstract public *boolean*  **isBuffering** ()

Check whether if frontend is buffering output



abstract public  **start** ()

Starts the frontend



abstract public *string*  **getContent** ()

Returns output cached content



abstract public  **stop** ()

Stops the frontend



abstract public  **beforeStore** (*mixed* $data)

Serializes data before storing it



abstract public  **afterRetrieve** (*mixed* $data)

Unserializes data after retrieving it



