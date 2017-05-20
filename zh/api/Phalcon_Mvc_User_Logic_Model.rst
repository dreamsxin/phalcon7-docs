Abstract class **Phalcon\\Mvc\\User\\Logic\\Model**
===================================================

*extends* abstract class :doc:`Phalcon\\Mvc\\User\\Logic <Phalcon_Mvc_User_Logic>`

*implements* :doc:`Phalcon\\Events\\EventsAwareInterface <Phalcon_Events_EventsAwareInterface>`, :doc:`Phalcon\\Di\\InjectionAwareInterface <Phalcon_Di_InjectionAwareInterface>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/mvc/user/logic/model.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Phalcon\\Mvc\\User\\Logic  This class can be used to provide user business logic an easy access to services in the application


Methods
-------

abstract public  **get** ([*unknown* $arguments])

...


abstract public  **getAll** ([*unknown* $arguments])

...


abstract public  **save** ([*unknown* $arguments])

...


abstract public  **create** ([*unknown* $arguments])

...


abstract public  **delete** ([*unknown* $arguments])

...


abstract public  **deleteAll** ([*unknown* $arguments])

...


abstract public  **update** ([*unknown* $arguments])

...


abstract public  **updateAll** ([*unknown* $arguments])

...


abstract public  **count** ([*unknown* $arguments])

...


public  **__construct** ([*string* $actionName], [*unknown* $arguments]) inherited from Phalcon\\User\\Logic

Constructor for Phalcon\\User\\Logic



public *string*  **getActionName** () inherited from Phalcon\\User\\Logic

Gets the action name



public *array*  **getActionParams** () inherited from Phalcon\\User\\Logic

Gets action params



public  **setContent** (*mixed* $content) inherited from Phalcon\\User\\Logic

Sets content



public *mixed*  **getContent** () inherited from Phalcon\\User\\Logic

Gets content



public static *object*  **call** ([*string* $actionName], [*unknown* $arguments]) inherited from Phalcon\\User\\Logic

Loads an logic and prepares it for manipulation



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


