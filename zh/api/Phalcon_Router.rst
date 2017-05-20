Abstract class **Phalcon\\Router**
==================================

*extends* abstract class :doc:`Phalcon\\Di\\Injectable <Phalcon_Di_Injectable>`

*implements* :doc:`Phalcon\\Events\\EventsAwareInterface <Phalcon_Events_EventsAwareInterface>`, :doc:`Phalcon\\Di\\InjectionAwareInterface <Phalcon_Di_InjectionAwareInterface>`, :doc:`Phalcon\\RouterInterface <Phalcon_RouterInterface>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/router.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Base class for Phalcon\\Router and Phalcon\\Mvc\\Router


Constants
---------

*integer* **MODE_DEFAULT**

*integer* **MODE_NONE**

*integer* **MODE_REST**

Methods
-------

public  **setDefaultModule** (*string* $moduleName)

Sets the name of the default module



public *string*  **getDefaultModule** ()

Gets the name of the default module



public  **setDefaultNamespace** (*string* $namespaceName)

Sets the name of the default namespace



public *string*  **getDefaultNamespace** ()

Gets the name of the default namespace



public  **setDefaultHandler** (*unknown* $handlerName)

Sets the default handle name



public *string*  **getDefaultHandler** ()

Gets the default handle name



public  **setDefaultAction** (*string* $actionName)

Sets the default action name



public *string*  **getDefaultAction** ()

Gets the default action name



public  **setDefaultParams** (*array* $params)

Sets the default extra params



public *string*  **getDefaultParams** ()

Gets the default extra params



public *string*  **setCaseSensitive** (*boolean* $caseSensitive)

Sets the case sensitive



public *boolean*  **getCaseSensitive** ()

Returns the case sensitive



public  **setMode** (*int* $mode)

Sets the mode



public  **getMode** ()

Gets the mode



public  **setModuleName** (*string* $moduleName)

Sets proccesed module name



public *string*  **getModuleName** ()

Returns proccesed module name



public  **setNamespaceName** (*string* $namespaceName)

Sets proccesed namespace name



public *string*  **getNamespaceName** ()

Returns proccesed namespace name



public  **setHandlerName** (*unknown* $handlerName)

Sets proccesed handle name



public *string*  **getHandlerName** ()

Returns proccesed handle name



public  **setActionName** (*string* $actionName)

Sets proccesed action name



public *string*  **getActionName** ()

Returns proccesed action name



public  **setParams** (*array* $params)

Sets proccesed extra params



public *array*  **getParams** ()

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


abstract public  **handle** ([*string* $uri]) inherited from Phalcon\\RouterInterface

Handles routing information received from the rewrite engine



