Class **Phalcon\\Cache\\Memory**
================================

*extends* abstract class :doc:`Phalcon\\DI\\Injectable <Phalcon_DI_Injectable>`

*implements* :doc:`Phalcon\\Events\\EventsAwareInterface <Phalcon_Events_EventsAwareInterface>`, :doc:`Phalcon\\DI\\InjectionAwareInterface <Phalcon_DI_InjectionAwareInterface>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/cache/memory.c" class="btn btn-default btn-sm">Source on GitHub</a>`

It can be used to replace APC or local memcached.


Methods
-------

public  **__construct** ([*string* $prefix])

Phalcon\\Cache\\Memory constructor



public :doc:`Phalcon\\Cache\\Memory <Phalcon_Cache_Memory>`  **set** (*string|array* $keys, [*mixed* $value], [*long* $lifetime])

Stores cached content



public *mixed*  **get** (*string|array* $keys)

Returns a cached content



public *boolean*  **delete** (*string|array* $keys, [*long* $lifetime])

Returns a cached content



public  **flush** ()

...


public  **dump** ([*unknown* $limit])

...


public  **__set** (*string* $key, *mixed* $value)

Stores cached content



public *mixed*  **__get** (*string* $key)

Returns a cached content



public  **setDI** (:doc:`Phalcon\\DiInterface <Phalcon_DiInterface>` $dependencyInjector) inherited from Phalcon\\DI\\Injectable

Sets the dependency injector



public :doc:`Phalcon\\DiInterface <Phalcon_DiInterface>`  **getDI** ([*unknown* $error], [*unknown* $notUseDefault]) inherited from Phalcon\\DI\\Injectable

Returns the internal dependency injector



public  **setEventsManager** (:doc:`Phalcon\\Events\\ManagerInterface <Phalcon_Events_ManagerInterface>` $eventsManager) inherited from Phalcon\\DI\\Injectable

Sets the event manager



public :doc:`Phalcon\\Events\\ManagerInterface <Phalcon_Events_ManagerInterface>`  **getEventsManager** () inherited from Phalcon\\DI\\Injectable

Returns the internal event manager



public *boolean*  **fireEvent** (*string* $eventName, [*unknown* $data], [*unknown* $cancelable]) inherited from Phalcon\\DI\\Injectable

Fires an event, implicitly calls behaviors and listeners in the events manager are notified



public *boolean*  **fireEventCancel** (*string* $eventName, [*unknown* $data], [*unknown* $cancelable]) inherited from Phalcon\\DI\\Injectable

Fires an event, implicitly calls behaviors and listeners in the events manager are notified This method stops if one of the callbacks/listeners returns boolean false



public *boolean*  **hasService** (*string* $name) inherited from Phalcon\\DI\\Injectable

Check whether the DI contains a service by a name



public *mixed*  **getResolveService** (*string* $name, [*unknown* $args], [*unknown* $noerror], [*unknown* $noshared]) inherited from Phalcon\\DI\\Injectable

Resolves the service based on its configuration



public  **__sleep** () inherited from Phalcon\\DI\\Injectable

...


public  **__debugInfo** () inherited from Phalcon\\DI\\Injectable

...


