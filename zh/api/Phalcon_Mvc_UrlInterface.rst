Interface **Phalcon\\Mvc\\UrlInterface**
========================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/phalcon/mvc/urlinterface.zep" class="btn btn-default btn-sm">Source on GitHub</a>`

Phalcon\\Mvc\\UrlInterface initializer


Methods
-------

abstract public  **setBaseUri** (*string* $baseUri)

Sets a prefix to all the urls generated



abstract public *string*  **getBaseUri** ()

Returns the prefix for all the generated urls. By default /



abstract public  **setBasePath** (*string* $basePath)

Sets a base paths for all the generated paths



abstract public *string*  **getBasePath** ()

Returns a base path



abstract public *string*  **get** ([*string|array* $uri], [*unknown* $args], [*unknown* $local])

Generates a URL



abstract public *string*  **path** ([*string* $path])

Generates a local path



