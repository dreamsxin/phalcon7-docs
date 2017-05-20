Class **Phalcon\\Loader**
=========================

*extends* abstract class :doc:`Phalcon\\Di\\Injectable <Phalcon_Di_Injectable>`

*implements* :doc:`Phalcon\\Events\\EventsAwareInterface <Phalcon_Events_EventsAwareInterface>`, :doc:`Phalcon\\Di\\InjectionAwareInterface <Phalcon_Di_InjectionAwareInterface>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/loader.c" class="btn btn-default btn-sm">Source on GitHub</a>`

This component helps to load your project classes automatically based on some conventions  

.. code-block:: php

    <?php

     //Creates the autoloader
     $loader = new Phalcon\Loader();
    
     //Register some namespaces
     $loader->registerNamespaces(array(
       'Example\Base' => 'vendor/example/base/',
       'Example\Adapter' => 'vendor/example/adapter/',
       'Example' => 'vendor/example/'
     ));
    
     //register autoloader
     $loader->register();
    
     //Requiring this class will automatically include file vendor/example/adapter/Some.php
     $adapter = Example\Adapter\Some();



Methods
-------

public  **__construct** ()

Phalcon\\Loader constructor



public :doc:`Phalcon\\Loader <Phalcon_Loader>`  **setExtensions** (*array* $extensions)

Sets an array of extensions that the loader must try in each attempt to locate the file



public *boolean*  **getExtensions** ()

Return file extensions registered in the loader



public :doc:`Phalcon\\Loader <Phalcon_Loader>`  **registerNamespaces** (*array* $namespaces, [*boolean* $merge])

Register namespaces and their related directories



public *array*  **getNamespaces** ()

Return current namespaces registered in the autoloader



public :doc:`Phalcon\\Loader <Phalcon_Loader>`  **registerPrefixes** (*array* $prefixes, [*boolean* $merge])

Register directories on which "not found" classes could be found



public  **getPrefixes** ()

Return current prefixes registered in the autoloader



public :doc:`Phalcon\\Loader <Phalcon_Loader>`  **registerDirs** (*array* $directories, [*boolean* $merge])

Register directories on which "not found" classes could be found



public  **getDirs** ()

Return current directories registered in the autoloader



public :doc:`Phalcon\\Loader <Phalcon_Loader>`  **registerClasses** (*array* $classes, [*boolean* $merge])

Register classes and their locations



public  **getClasses** ()

Return the current class-map registered in the autoloader



public :doc:`Phalcon\\Loader <Phalcon_Loader>`  **register** ()

Register the autoload method



public :doc:`Phalcon\\Loader <Phalcon_Loader>`  **unregister** ()

Unregister the autoload method



public *boolean*  **findFile** (*string* $className, *array|string* $directory, *array* $extensions, [*string* $ds])

Makes the work of autoload registered classes



public *boolean*  **autoLoad** (*string* $className)

Makes the work of autoload registered classes



public *string*  **getFoundPath** ()

Get the path when a class was found



public *string*  **getCheckedPath** ()

Get the path the loader is checking for a path



public static :doc:`Phalcon\\Loader <Phalcon_Loader>`  **getDefault** ()

Return the default loader



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


