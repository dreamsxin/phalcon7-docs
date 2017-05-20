Class **Phalcon\\Cli\\Router**
==============================

*extends* abstract class :doc:`Phalcon\\Router <Phalcon_Router>`

*implements* :doc:`Phalcon\\RouterInterface <Phalcon_RouterInterface>`, :doc:`Phalcon\\Di\\InjectionAwareInterface <Phalcon_Di_InjectionAwareInterface>`, :doc:`Phalcon\\Events\\EventsAwareInterface <Phalcon_Events_EventsAwareInterface>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/cli/router.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Phalcon\\Cli\\Router is the standard framework router. Routing is the process of taking a command-line arguments and decomposing it into parameters to determine which module, task, and action of that task should receive the request    

.. code-block:: php

    <?php

    $router = new Phalcon\Cli\Router();
    $router->handle(array(
    	'module' => 'main',
    	'task' => 'videos',
    	'action' => 'process'
    ));
    echo $router->getTaskName();



Constants
---------

*integer* **MODE_DEFAULT**

*integer* **MODE_NONE**

*integer* **MODE_REST**

Methods
-------

public  **__construct** ()

Phalcon\\Cli\\Router constructor



public  **setDefaultTask** (*unknown* $handlerName)

Sets the default task name



public *string*  **getTaskName** ()

Returns proccesed task name



public  **handle** ([*array* $arguments])

Handles routing information received from command-line arguments



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


