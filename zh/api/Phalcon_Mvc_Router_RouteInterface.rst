Interface **Phalcon\\Mvc\\Router\\RouteInterface**
==================================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/phalcon/mvc/router/routeinterface.zep" class="btn btn-default btn-sm">Source on GitHub</a>`

Phalcon\\Mvc\\Router\\RouteInterface initializer


Methods
-------

abstract public *string*  **compilePattern** (*string* $pattern, [*unknown* $regex])

Replaces placeholders from pattern returning a valid PCRE regular expression



abstract public  **via** (*string|array* $httpMethods)

Set one or more HTTP methods that constraint the matching of the route



abstract public  **reConfigure** (*string* $pattern, [*array* $paths], [*unknown* $regex])

Reconfigure the route adding a new pattern and a set of paths



abstract public *string*  **getName** ()

Returns the route's name



abstract public  **setName** (*string* $name)

Sets the route's name



abstract public  **setHttpMethods** (*string|array* $httpMethods)

Sets a set of HTTP methods that constraint the matching of the route



abstract public *string*  **getRouteId** ()

Returns the route's id



abstract public *string*  **getPattern** ()

Returns the route's pattern



abstract public *string*  **getCompiledPattern** ()

Returns the route's pattern



abstract public *array*  **getPaths** ()

Returns the paths



abstract public *string|array*  **getHttpMethods** ()

Returns the HTTP methods that constraint matching the route



abstract public static  **reset** ()

Resets the internal route id generator



