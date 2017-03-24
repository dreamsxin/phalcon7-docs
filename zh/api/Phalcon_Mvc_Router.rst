Class **Phalcon\\Mvc\\Router**
==============================

*extends* abstract class :doc:`Phalcon\\Di\\Injectable <Phalcon_Di_Injectable>`

*implements* :doc:`Phalcon\\Events\\EventsAwareInterface <Phalcon_Events_EventsAwareInterface>`, :doc:`Phalcon\\Di\\InjectionAwareInterface <Phalcon_Di_InjectionAwareInterface>`, :doc:`Phalcon\\Mvc\\RouterInterface <Phalcon_Mvc_RouterInterface>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/mvc/router.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Phalcon\\Mvc\\Router is the standard framework router. Routing is the process of taking a URI endpoint (that part of the URI which comes after the base URL) and decomposing it into parameters to determine which module, controller, and action of that controller should receive the request    

.. code-block:: php

    <?php

    $router = new Phalcon\Mvc\Router();
    
      $router->add(
    	"/documentation/{chapter}/{name}.{type:[a-z]+}",
    	array(
    		"controller" => "documentation",
    		"action"     => "show"
    	)
    );
    
    $router->handle();
    
    echo $router->getControllerName();



Constants
---------

*integer* **URI_SOURCE_GET_URL**

*integer* **URI_SOURCE_SERVER_REQUEST_URI**

Methods
-------

public  **__construct** ([*boolean* $defaultRoutes])

Phalcon\\Mvc\\Router constructor



public *string*  **getRewriteUri** ()

Get rewrite info. This info is read from $_GET['_url']. This returns '/' if the rewrite information cannot be read



public :doc:`Phalcon\\Mvc\\Router <Phalcon_Mvc_Router>`  **setUriSource** (*int* $uriSource)

Sets the URI source. One of the URI_SOURCE_* constants 

.. code-block:: php

    <?php

    $router->setUriSource(Router::URI_SOURCE_SERVER_REQUEST_URI);




public :doc:`Phalcon\\Mvc\\Router <Phalcon_Mvc_Router>`  **removeExtraSlashes** (*boolean* $remove)

Set whether router must remove the extra slashes in the handled routes



public :doc:`Phalcon\\Mvc\\Router <Phalcon_Mvc_Router>`  **setDefaultNamespace** (*string* $namespaceName)

Sets the name of the default namespace



public *string*  **getDefaultNamespace** ()

Returns the name of the default namespace



public :doc:`Phalcon\\Mvc\\Router <Phalcon_Mvc_Router>`  **setDefaultModule** (*string* $moduleName)

Sets the name of the default module



public *string*  **getDefaultModule** ()

Returns the name of the default module



public :doc:`Phalcon\\Mvc\\Router <Phalcon_Mvc_Router>`  **setDefaultController** (*string* $controllerName)

Sets the default controller name



public *string*  **getDefaultController** ()

Returns the default controller name



public :doc:`Phalcon\\Mvc\\Router <Phalcon_Mvc_Router>`  **setDefaultAction** (*string* $actionName)

Sets the default action name



public *string*  **getDefaultAction** ()

Returns the default action name



public :doc:`Phalcon\\Mvc\\Router <Phalcon_Mvc_Router>`  **setDefaults** (*array* $defaults)

Sets an array of default paths. If a route is missing a path the router will use the defined here This method must not be used to set a 404 route 

.. code-block:: php

    <?php

     $router->setDefaults(array(
    	'module' => 'common',
    	'action' => 'index'
     ));




public *array*  **getDefaults** ()

Returns an array of default parameters



public  **handle** ([*string* $uri])

Handles routing information received from the rewrite engine 

.. code-block:: php

    <?php

     //Read the info from the rewrite engine
     $router->handle();
    
     //Manually passing an URL
     $router->handle('/posts/edit/1');




public :doc:`Phalcon\\Mvc\\Router\\Route <Phalcon_Mvc_Router_Route>`  **add** (*string* $pattern, [*string/array* $paths], [*array* $regex], [*string* $httpMethods])

Adds a route to the router without any HTTP constraint 

.. code-block:: php

    <?php

     $router->add('/about', 'About::index');




public :doc:`Phalcon\\Mvc\\Router\\Route <Phalcon_Mvc_Router_Route>`  **addGet** (*string* $pattern, [*string/array* $paths], [*unknown* $regex])

Adds a route to the router that only match if the HTTP method is GET



public :doc:`Phalcon\\Mvc\\Router\\Route <Phalcon_Mvc_Router_Route>`  **addPost** (*string* $pattern, [*string/array* $paths], [*unknown* $regex])

Adds a route to the router that only match if the HTTP method is POST



public :doc:`Phalcon\\Mvc\\Router\\Route <Phalcon_Mvc_Router_Route>`  **addPut** (*string* $pattern, [*string/array* $paths], [*unknown* $regex])

Adds a route to the router that only match if the HTTP method is PUT



public :doc:`Phalcon\\Mvc\\Router\\Route <Phalcon_Mvc_Router_Route>`  **addPatch** (*string* $pattern, [*string/array* $paths], [*unknown* $regex])

Adds a route to the router that only match if the HTTP method is PATCH



public :doc:`Phalcon\\Mvc\\Router\\Route <Phalcon_Mvc_Router_Route>`  **addDelete** (*string* $pattern, [*string/array* $paths], [*unknown* $regex])

Adds a route to the router that only match if the HTTP method is DELETE



public :doc:`Phalcon\\Mvc\\Router\\Route <Phalcon_Mvc_Router_Route>`  **addOptions** (*string* $pattern, [*string/array* $paths], [*unknown* $regex])

Add a route to the router that only match if the HTTP method is OPTIONS



public :doc:`Phalcon\\Mvc\\Router\\Route <Phalcon_Mvc_Router_Route>`  **addHead** (*string* $pattern, [*string/array* $paths], [*unknown* $regex])

Adds a route to the router that only match if the HTTP method is HEAD



public :doc:`Phalcon\\Mvc\\Router <Phalcon_Mvc_Router>`  **mount** (:doc:`Phalcon\\Mvc\\Router\\Group <Phalcon_Mvc_Router_Group>` $group)

Mounts a group of routes in the router



public :doc:`Phalcon\\Mvc\\Router <Phalcon_Mvc_Router>`  **notFound** (*array|string* $paths)

Set a group of paths to be returned when none of the defined routes are matched



public  **clear** ()

Removes all the pre-defined routes



public :doc:`Phalcon\\Mvc\\Router <Phalcon_Mvc_Router>`  **setNamespaceName** (*string* $namespaceName)

Sets the name of the namespace



public *string*  **getNamespaceName** ()

Returns the processed namespace name



public :doc:`Phalcon\\Mvc\\Router <Phalcon_Mvc_Router>`  **setModuleName** (*string* $moduleName)

Sets the name of the module



public *string*  **getModuleName** ()

Returns the processed module name



public :doc:`Phalcon\\Mvc\\Router <Phalcon_Mvc_Router>`  **setControllerName** (*string* $controllerName)

Sets the name of the controller



public *string*  **getControllerName** ()

Returns the processed controller name



public :doc:`Phalcon\\Mvc\\Router <Phalcon_Mvc_Router>`  **setActionName** (*string* $actionName)

Sets the name of the action



public *string*  **getActionName** ()

Returns the processed action name



public :doc:`Phalcon\\Mvc\\Router <Phalcon_Mvc_Router>`  **setParams** (*array* $params)

Sets the params



public *array*  **getParams** ()

Returns the processed parameters



public :doc:`Phalcon\\Mvc\\Router\\Route <Phalcon_Mvc_Router_Route>`  **getMatchedRoute** ()

Returns the route that matchs the handled URI



public *array*  **getMatches** ()

Returns the sub expressions in the regular expression matched



public *boolean*  **wasMatched** ()

Checks if the router macthes any of the defined routes



public :doc:`Phalcon\\Mvc\\Router\\Route <Phalcon_Mvc_Router_Route>` [] **getRoutes** ()

Returns all the routes defined in the router



public :doc:`Phalcon\\Mvc\\Router\\Route <Phalcon_Mvc_Router_Route>`  | false **getRouteById** (*string* $id)

Returns a route object by its id



public :doc:`Phalcon\\Mvc\\Router\\Route <Phalcon_Mvc_Router_Route>`  **getRouteByName** (*string* $name)

Returns a route object by its name



public  **isExactControllerName** ()

Returns whether controller name should not be mangled



public  **setDI** (:doc:`Phalcon\\DiInterface <Phalcon_DiInterface>` $dependencyInjector) inherited from Phalcon\\Di\\Injectable

Sets the dependency injector



public :doc:`Phalcon\\DiInterface <Phalcon_DiInterface>`  **getDI** ([*unknown* $error], [*unknown* $notUseDefault]) inherited from Phalcon\\Di\\Injectable

Returns the internal dependency injector



public  **setEventsManager** (:doc:`Phalcon\\Events\\ManagerInterface <Phalcon_Events_ManagerInterface>` $eventsManager) inherited from Phalcon\\Di\\Injectable

Sets the event manager



public :doc:`Phalcon\\Events\\ManagerInterface <Phalcon_Events_ManagerInterface>`  **getEventsManager** () inherited from Phalcon\\Di\\Injectable

Returns the internal event manager



public *boolean*  **fireEvent** (*string* $eventName, [*unknown* $data], [*unknown* $cancelable]) inherited from Phalcon\\Di\\Injectable

Fires an event, implicitly calls behaviors and listeners in the events manager are notified



public *boolean*  **fireEventCancel** (*string* $eventName, [*unknown* $data], [*unknown* $cancelable]) inherited from Phalcon\\Di\\Injectable

Fires an event, implicitly calls behaviors and listeners in the events manager are notified This method stops if one of the callbacks/listeners returns boolean false



public *boolean*  **hasService** (*string* $name) inherited from Phalcon\\Di\\Injectable

Check whether the DI contains a service by a name



public *mixed*  **getResolveService** (*string* $name, [*unknown* $args], [*unknown* $noerror], [*unknown* $noshared]) inherited from Phalcon\\Di\\Injectable

Resolves the service based on its configuration



public  **__get** (*unknown* $property) inherited from Phalcon\\Di\\Injectable

Magic method __get



public  **__sleep** () inherited from Phalcon\\Di\\Injectable

...


public  **__debugInfo** () inherited from Phalcon\\Di\\Injectable

...


