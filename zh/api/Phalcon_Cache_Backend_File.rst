Class **Phalcon\\Cache\\Backend\\File**
=======================================

*extends* abstract class :doc:`Phalcon\\Cache\\Backend <Phalcon_Cache_Backend>`

*implements* :doc:`Phalcon\\Cache\\BackendInterface <Phalcon_Cache_BackendInterface>`, :doc:`Phalcon\\Di\\InjectionAwareInterface <Phalcon_Di_InjectionAwareInterface>`, :doc:`Phalcon\\Events\\EventsAwareInterface <Phalcon_Events_EventsAwareInterface>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/cache/backend/file.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Allows to cache output fragments using a file backend  

.. code-block:: php

    <?php

    //Cache the file for 2 days
    $frontendOptions = array(
    	'lifetime' => 172800
    );
    
      //Create a output cache
      $frontCache = \Phalcon\Cache\Frontend\Output($frontOptions);
    
    //Set the cache directory
    $backendOptions = array(
    	'cacheDir' => '../app/cache/'
    );
    
      //Create the File backend
      $cache = new \Phalcon\Cache\Backend\File($frontCache, $backendOptions);
    
    $content = $cache->start('my-cache');
    if ($content === null) {
      	echo '<h1>', time(), '</h1>';
      	$cache->save();
    } else {
    	echo $content;
    }



Methods
-------

public  **__construct** (:doc:`Phalcon\\Cache\\FrontendInterface <Phalcon_Cache_FrontendInterface>` $frontend, *array* $options)

Phalcon\\Cache\\Backend\\File constructor



public *mixed*  **get** (*string* $keyName)

Returns a cached content



public  **save** ([*string* $keyName], [*unknown* $value], [*long* $lifetime], [*boolean* $stopBuffer])

Stores cached content into the file backend and stops the frontend



public *boolean*  **delete** (*string* $keyName)

Deletes a value from the cache by its key



public *array*  **queryKeys** ([*string* $prefix])

Query the existing cached keys



public *boolean*  **exists** (*string* $keyName)

Checks if cache exists and it isn't expired



public *mixed*  **increment** (*string* $keyName, [*long* $value])

Increment of a given key, by number $value



public *mixed*  **decrement** (*string* $keyName, [*long* $value])

Decrement of a given key, by number $value



public *boolean*  **flush** ()

Immediately invalidates all existing items.



public *mixed*  **start** (*int|string* $keyName, [*long* $lifetime]) inherited from Phalcon\\Cache\\Backend

Starts a cache. The $keyname allows to identify the created fragment



public  **stop** ([*boolean* $stopBuffer]) inherited from Phalcon\\Cache\\Backend

Stops the frontend without store any cached content



public *mixed*  **getFrontend** () inherited from Phalcon\\Cache\\Backend

Returns front-end instance adapter related to the back-end



public *array*  **getOptions** () inherited from Phalcon\\Cache\\Backend

Returns the backend options



public *boolean*  **isFresh** () inherited from Phalcon\\Cache\\Backend

Checks whether the last cache is fresh or cached



public *boolean*  **isStarted** () inherited from Phalcon\\Cache\\Backend

Checks whether the cache has starting buffering or not



public *int*  **getLifetime** () inherited from Phalcon\\Cache\\Backend

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


