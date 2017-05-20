Class **Phalcon\\Mvc\\Router\\Annotations**
===========================================

*extends* class :doc:`Phalcon\\Mvc\\Router <Phalcon_Mvc_Router>`

*implements* :doc:`Phalcon\\Mvc\\RouterInterface <Phalcon_Mvc_RouterInterface>`, :doc:`Phalcon\\Events\\EventsAwareInterface <Phalcon_Events_EventsAwareInterface>`, :doc:`Phalcon\\Di\\InjectionAwareInterface <Phalcon_Di_InjectionAwareInterface>`, :doc:`Phalcon\\RouterInterface <Phalcon_RouterInterface>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/mvc/router/annotations.c" class="btn btn-default btn-sm">Source on GitHub</a>`

A router that reads routes annotations from classes/resources  

.. code-block:: php

    <?php

     $di['router'] = function() {
    
    	//Use the annotations router
    	$router = new \Phalcon\Mvc\Router\Annotations(false);
    
    	//This will do the same as above but only if the handled uri starts with /robots
     		$router->addResource('Robots', '/robots');
    
     		return $router;
    };



Constants
---------

*integer* **MODE_DEFAULT**

*integer* **MODE_NONE**

*integer* **MODE_REST**

*integer* **URI_SOURCE_GET_URL**

*integer* **URI_SOURCE_SERVER_REQUEST_URI**

Methods
-------

public :doc:`Phalcon\\Mvc\\Router\\Annotations <Phalcon_Mvc_Router_Annotations>`  **addResource** (*string* $handler, [*string* $prefix])

Adds a resource to the annotations handler A resource is a class that contains routing annotations



public :doc:`Phalcon\\Mvc\\Router\\Annotations <Phalcon_Mvc_Router_Annotations>`  **addModuleResource** (*string* $module, *string* $handler, [*string* $prefix])

Adds a resource to the annotations handler A resource is a class that contains routing annotations The class is located in a module



public  **handle** ([*string* $uri])

Produce the routing parameters from the rewrite information



public  **processControllerAnnotation** (*string* $handler, *unknown* $annotation)

Checks for annotations in the controller docblock



public  **processActionAnnotation** (*string* $module, *string* $namespace, *string* $controller, *string* $action, :doc:`Phalcon\\Annotations\\Annotation <Phalcon_Annotations_Annotation>` $annotation)

Checks for annotations in the public methods of the controller



public  **setControllerSuffix** (*string* $controllerSuffix)

Changes the controller class suffix



public  **setActionSuffix** (*string* $actionSuffix)

Changes the action method suffix



public *array*  **getResources** ()

Return the registered resources



public  **__construct** ([*boolean* $defaultRoutes]) inherited from Phalcon\\Mvc\\Router

Phalcon\\Mvc\\Router constructor



public *string*  **getRewriteUri** () inherited from Phalcon\\Mvc\\Router

Get rewrite info. This info is read from $_GET['_url']. This returns '/' if the rewrite information cannot be read



public :doc:`Phalcon\\Mvc\\Router <Phalcon_Mvc_Router>`  **setUriSource** (*int* $uriSource) inherited from Phalcon\\Mvc\\Router

Sets the URI source. One of the URI_SOURCE_* constants 

.. code-block:: php

    <?php

    $router->setUriSource(Router::URI_SOURCE_SERVER_REQUEST_URI);




public :doc:`Phalcon\\Mvc\\Router <Phalcon_Mvc_Router>`  **removeExtraSlashes** (*boolean* $remove) inherited from Phalcon\\Mvc\\Router

Set whether router must remove the extra slashes in the handled routes



public :doc:`Phalcon\\Mvc\\Router <Phalcon_Mvc_Router>`  **setDefaults** (*array* $defaults) inherited from Phalcon\\Mvc\\Router

Sets an array of default paths. If a route is missing a path the router will use the defined here This method must not be used to set a 404 route 

.. code-block:: php

    <?php

     $router->setDefaults(array(
    	'module' => 'common',
    	'action' => 'index'
     ));




public *array*  **getDefaults** () inherited from Phalcon\\Mvc\\Router

Returns an array of default parameters



public :doc:`Phalcon\\Mvc\\Router\\Route <Phalcon_Mvc_Router_Route>`  **add** (*string* $pattern, [*string/array* $paths], [*array* $regex], [*string* $httpMethods]) inherited from Phalcon\\Mvc\\Router

Adds a route to the router without any HTTP constraint 

.. code-block:: php

    <?php

     $router->add('/about', 'About::index');




public :doc:`Phalcon\\Mvc\\Router\\Route <Phalcon_Mvc_Router_Route>`  **addGet** (*string* $pattern, [*string/array* $paths], [*unknown* $regex]) inherited from Phalcon\\Mvc\\Router

Adds a route to the router that only match if the HTTP method is GET



public :doc:`Phalcon\\Mvc\\Router\\Route <Phalcon_Mvc_Router_Route>`  **addPost** (*string* $pattern, [*string/array* $paths], [*unknown* $regex]) inherited from Phalcon\\Mvc\\Router

Adds a route to the router that only match if the HTTP method is POST



public :doc:`Phalcon\\Mvc\\Router\\Route <Phalcon_Mvc_Router_Route>`  **addPut** (*string* $pattern, [*string/array* $paths], [*unknown* $regex]) inherited from Phalcon\\Mvc\\Router

Adds a route to the router that only match if the HTTP method is PUT



public :doc:`Phalcon\\Mvc\\Router\\Route <Phalcon_Mvc_Router_Route>`  **addPatch** (*string* $pattern, [*string/array* $paths], [*unknown* $regex]) inherited from Phalcon\\Mvc\\Router

Adds a route to the router that only match if the HTTP method is PATCH



public :doc:`Phalcon\\Mvc\\Router\\Route <Phalcon_Mvc_Router_Route>`  **addDelete** (*string* $pattern, [*string/array* $paths], [*unknown* $regex]) inherited from Phalcon\\Mvc\\Router

Adds a route to the router that only match if the HTTP method is DELETE



public :doc:`Phalcon\\Mvc\\Router\\Route <Phalcon_Mvc_Router_Route>`  **addOptions** (*string* $pattern, [*string/array* $paths], [*unknown* $regex]) inherited from Phalcon\\Mvc\\Router

Add a route to the router that only match if the HTTP method is OPTIONS



public :doc:`Phalcon\\Mvc\\Router\\Route <Phalcon_Mvc_Router_Route>`  **addHead** (*string* $pattern, [*string/array* $paths], [*unknown* $regex]) inherited from Phalcon\\Mvc\\Router

Adds a route to the router that only match if the HTTP method is HEAD



public :doc:`Phalcon\\Mvc\\Router <Phalcon_Mvc_Router>`  **mount** (:doc:`Phalcon\\Mvc\\Router\\Group <Phalcon_Mvc_Router_Group>` $group) inherited from Phalcon\\Mvc\\Router

Mounts a group of routes in the router



public :doc:`Phalcon\\Mvc\\Router <Phalcon_Mvc_Router>`  **notFound** (*array|string* $paths) inherited from Phalcon\\Mvc\\Router

Set a group of paths to be returned when none of the defined routes are matched



public  **clear** () inherited from Phalcon\\Mvc\\Router

Removes all the pre-defined routes



public :doc:`Phalcon\\Mvc\\Router\\Route <Phalcon_Mvc_Router_Route>`  **getMatchedRoute** () inherited from Phalcon\\Mvc\\Router

Returns the route that matchs the handled URI



public *array*  **getMatches** () inherited from Phalcon\\Mvc\\Router

Returns the sub expressions in the regular expression matched



public *boolean*  **wasMatched** () inherited from Phalcon\\Mvc\\Router

Checks if the router macthes any of the defined routes



public :doc:`Phalcon\\Mvc\\Router\\Route <Phalcon_Mvc_Router_Route>` [] **getRoutes** () inherited from Phalcon\\Mvc\\Router

Returns all the routes defined in the router



public :doc:`Phalcon\\Mvc\\Router\\Route <Phalcon_Mvc_Router_Route>`  | false **getRouteById** (*string* $id) inherited from Phalcon\\Mvc\\Router

Returns a route object by its id



public :doc:`Phalcon\\Mvc\\Router\\Route <Phalcon_Mvc_Router_Route>`  **getRouteByName** (*string* $name) inherited from Phalcon\\Mvc\\Router

Returns a route object by its name



public  **isExactControllerName** () inherited from Phalcon\\Mvc\\Router

Returns whether controller name should not be mangled



public  **setDefaultController** (*unknown* $handlerName) inherited from Phalcon\\Mvc\\Router

Sets the default controller name



public *string*  **getDefaultController** () inherited from Phalcon\\Mvc\\Router

Gets the default controller name



public  **setControllerName** (*unknown* $handlerName) inherited from Phalcon\\Mvc\\Router

Sets the controller name



public *string*  **getControllerName** () inherited from Phalcon\\Mvc\\Router

Gets the controller name



public  **setDefaultModule** (*string* $moduleName) inherited from Phalcon\\Router

Sets the name of the default module



public *string*  **getDefaultModule** () inherited from Phalcon\\Router

Gets the name of the default module



public  **setDefaultNamespace** (*string* $namespaceName) inherited from Phalcon\\Router

Sets the name of the default namespace



public *string*  **getDefaultNamespace** () inherited from Phalcon\\Router

Gets the name of the default namespace



public  **setDefaultHandler** (*unknown* $handlerName) inherited from Phalcon\\Router

Sets the default handle name



public *string*  **getDefaultHandler** () inherited from Phalcon\\Router

Gets the default handle name



public  **setDefaultAction** (*string* $actionName) inherited from Phalcon\\Router

Sets the default action name



public *string*  **getDefaultAction** () inherited from Phalcon\\Router

Gets the default action name



public  **setDefaultParams** (*array* $params) inherited from Phalcon\\Router

Sets the default extra params



public *string*  **getDefaultParams** () inherited from Phalcon\\Router

Gets the default extra params



public *string*  **setCaseSensitive** (*boolean* $caseSensitive) inherited from Phalcon\\Router

Sets the case sensitive



public *boolean*  **getCaseSensitive** () inherited from Phalcon\\Router

Returns the case sensitive



public  **setMode** (*int* $mode) inherited from Phalcon\\Router

Sets the mode



public  **getMode** () inherited from Phalcon\\Router

Gets the mode



public  **setModuleName** (*string* $moduleName) inherited from Phalcon\\Router

Sets proccesed module name



public *string*  **getModuleName** () inherited from Phalcon\\Router

Returns proccesed module name



public  **setNamespaceName** (*string* $namespaceName) inherited from Phalcon\\Router

Sets proccesed namespace name



public *string*  **getNamespaceName** () inherited from Phalcon\\Router

Returns proccesed namespace name



public  **setHandlerName** (*unknown* $handlerName) inherited from Phalcon\\Router

Sets proccesed handle name



public *string*  **getHandlerName** () inherited from Phalcon\\Router

Returns proccesed handle name



public  **setActionName** (*string* $actionName) inherited from Phalcon\\Router

Sets proccesed action name



public *string*  **getActionName** () inherited from Phalcon\\Router

Returns proccesed action name



public  **setParams** (*array* $params) inherited from Phalcon\\Router

Sets proccesed extra params



public *array*  **getParams** () inherited from Phalcon\\Router

Returns proccesed extra params



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



public *mixed*  **fireEventData** (*string* $eventName, [*mixed* $data]) inherited from Phalcon\\Di\\Injectable

Fires an event, return data



public *boolean*  **hasService** (*string* $name) inherited from Phalcon\\Di\\Injectable

Check whether the DI contains a service by a name



public :doc:`Phalcon\\Di\\ServiceInterface <Phalcon_Di_ServiceInterface>`  **setService** (*unknown* $name) inherited from Phalcon\\Di\\Injectable

Sets a service from the DI



public *object|null*  **getService** (*unknown* $name) inherited from Phalcon\\Di\\Injectable

Obtains a service from the DI



public *mixed*  **getResolveService** (*string* $name, [*unknown* $args], [*unknown* $noerror], [*unknown* $noshared]) inherited from Phalcon\\Di\\Injectable

Resolves the service based on its configuration



public  **attachEvent** (*string* $eventType, *Closure* $callback) inherited from Phalcon\\Di\\Injectable

Attach a listener to the events



public  **__get** (*unknown* $property) inherited from Phalcon\\Di\\Injectable

Magic method __get



public  **__sleep** () inherited from Phalcon\\Di\\Injectable

...


public  **__debugInfo** () inherited from Phalcon\\Di\\Injectable

...


