Abstract class **Phalcon\\Cache\\Backend**
==========================================

*extends* abstract class :doc:`Phalcon\\Di\\Injectable <Phalcon_Di_Injectable>`

*implements* :doc:`Phalcon\\Events\\EventsAwareInterface <Phalcon_Events_EventsAwareInterface>`, :doc:`Phalcon\\Di\\InjectionAwareInterface <Phalcon_Di_InjectionAwareInterface>`, :doc:`Phalcon\\Cache\\BackendInterface <Phalcon_Cache_BackendInterface>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/cache/backend.c" class="btn btn-default btn-sm">Source on GitHub</a>`

This class implements common functionality for backend adapters. A backend cache adapter may extend this class


Methods
-------

public  **__construct** (:doc:`Phalcon\\Cache\\FrontendInterface <Phalcon_Cache_FrontendInterface>` $frontend, [*array* $options])

Phalcon\\Cache\\Backend constructor



public *mixed*  **start** (*int|string* $keyName, [*long* $lifetime])

Starts a cache. The $keyname allows to identify the created fragment



public  **stop** ([*boolean* $stopBuffer])

Stops the frontend without store any cached content



public *mixed*  **getFrontend** ()

Returns front-end instance adapter related to the back-end



public *array*  **getOptions** ()

Returns the backend options



public *boolean*  **isFresh** ()

Checks whether the last cache is fresh or cached



public *boolean*  **isStarted** ()

Checks whether the cache has starting buffering or not



public *int*  **getLifetime** ()

Gets the last lifetime set



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


abstract public *mixed*  **get** (*string* $keyName) inherited from Phalcon\\Cache\\BackendInterface

Returns a cached content



abstract public  **save** ([*string* $keyName], [*unknown* $value], [*long* $lifetime], [*boolean* $stopBuffer]) inherited from Phalcon\\Cache\\BackendInterface

Stores cached content into the file backend and stops the frontend



abstract public *boolean*  **delete** (*string* $keyName) inherited from Phalcon\\Cache\\BackendInterface

Deletes a value from the cache by its key



abstract public *array*  **queryKeys** ([*string* $prefix]) inherited from Phalcon\\Cache\\BackendInterface

Query the existing cached keys



abstract public *boolean*  **exists** (*string* $keyName) inherited from Phalcon\\Cache\\BackendInterface

Checks if cache exists and it hasn't expired



abstract public *boolean*  **flush** () inherited from Phalcon\\Cache\\BackendInterface

Immediately invalidates all existing items.



