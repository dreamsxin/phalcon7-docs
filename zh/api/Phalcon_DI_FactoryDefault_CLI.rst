Class **Phalcon\\Di\\FactoryDefault\\CLI**
==========================================

*extends* class :doc:`Phalcon\\Di\\FactoryDefault <Phalcon_Di_FactoryDefault>`

*implements* :doc:`Phalcon\\DiInterface <Phalcon_DiInterface>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/di/factorydefault/cli.c" class="btn btn-default btn-sm">Source on GitHub</a>`

This is a variant of the standard Phalcon\\Di. By default it automatically registers all the services provided by the framework. Thanks to this, the developer does not need to register each service individually. This class is specially suitable for CLI applications


Methods
-------

public  **__construct** ()

Phalcon\\Di\\FactoryDefault\\CLI constructor



public *String*  **getName** () inherited from Phalcon\\Di

Returns the name



protected  **setEventsManager** () inherited from Phalcon\\Di

Sets a custom events manager



protected :doc:`Phalcon\\Events\\ManagerInterface <Phalcon_Events_ManagerInterface>`  **getEventsManager** () inherited from Phalcon\\Di

Returns the custom events manager



public :doc:`Phalcon\\Di\\ServiceInterface <Phalcon_Di_ServiceInterface>`  **set** (*string* $name, *mixed* $definition, [*boolean* $shared]) inherited from Phalcon\\Di

Registers a service in the services container



public  **remove** (*string* $name) inherited from Phalcon\\Di

Removes a service in the services container



public :doc:`Phalcon\\Di\\ServiceInterface <Phalcon_Di_ServiceInterface>`  **setRaw** (*string* $name, [*mixed* $definition], [*boolean* $shared]) inherited from Phalcon\\Di

Returns a service definition without resolving



public *mixed*  **getRaw** (*string* $name) inherited from Phalcon\\Di

Returns a service definition without resolving



public :doc:`Phalcon\\Di\\ServiceInterface <Phalcon_Di_ServiceInterface>`  **getService** (*string* $name) inherited from Phalcon\\Di

Returns a Phalcon\\Di\\Service instance



public :doc:`Phalcon\\Di\\ServiceInterface <Phalcon_Di_ServiceInterface>`  **setService** (*string* $name, :doc:`Phalcon\\Di\\ServiceInterface <Phalcon_Di_ServiceInterface>` $rawDefinition) inherited from Phalcon\\Di

Sets a service using a raw Phalcon\\Di\\Service definition



public *mixed*  **get** (*string* $name, [*array* $parameters], [*boolean* $noError], [*unknown* $noerror]) inherited from Phalcon\\Di

Resolves the service based on its configuration



public *mixed*  **getShared** (*string* $name, [*array* $parameters], [*boolean* $noError]) inherited from Phalcon\\Di

Resolves a service, the resolved service is stored in the DI, subsequent requests for this service will return the same instance



public *boolean*  **has** (*string* $name) inherited from Phalcon\\Di

Check whether the DI contains a service by a name



public *boolean*  **wasFreshInstance** () inherited from Phalcon\\Di

Check whether the last service obtained via getShared produced a fresh instance or an existing one



public :doc:`Phalcon\\Di\\Service <Phalcon_Di_Service>` [] **getServices** () inherited from Phalcon\\Di

Return the services registered in the DI



public static  **setDefault** (:doc:`Phalcon\\DiInterface <Phalcon_DiInterface>` $dependencyInjector) inherited from Phalcon\\Di

Set a default dependency injection container to be obtained into static methods



public static :doc:`Phalcon\\DiInterface <Phalcon_DiInterface>`  **getDefault** () inherited from Phalcon\\Di

Return the lastest DI created



public static  **reset** () inherited from Phalcon\\Di

Resets the internal default DI



public :doc:`Phalcon\\Di\\ServiceInterface <Phalcon_Di_ServiceInterface>`  **attempt** (*string* $name, *mixed* $definition, [*boolean* $shared]) inherited from Phalcon\\Di

Attempts to register a service in the services container Only is successful if a service hasn't been registered previously with the same name



public :doc:`Phalcon\\Di\\ServiceInterface <Phalcon_Di_ServiceInterface>`  **setShared** (*string* $name, *mixed* $definition) inherited from Phalcon\\Di

Registers an "always shared" service in the services container



public *boolean*  **offsetExists** (*unknown* $property) inherited from Phalcon\\Di

Check if a service is registered using the array syntax. Alias for Phalcon\\Di::has()



public  **offsetSet** (*unknown* $property, *unknown* $value) inherited from Phalcon\\Di

Allows to register a shared service using the array syntax. Alias for Phalcon\\Di::setShared() 

.. code-block:: php

    <?php

    $di['request'] = new Phalcon\Http\Request();




public *mixed*  **offsetGet** (*unknown* $property) inherited from Phalcon\\Di

Allows to obtain a shared service using the array syntax. Alias for Phalcon\\Di::getShared() 

.. code-block:: php

    <?php

    var_dump($di['request']);




public  **offsetUnset** (*unknown* $property) inherited from Phalcon\\Di

Removes a service from the services container using the array syntax. Alias for Phalcon\\Di::remove()



public *mixed*  **__call** (*string* $method, [*array* $arguments]) inherited from Phalcon\\Di

Magic method to get or set services using setters/getters



public  **__clone** () inherited from Phalcon\\Di

...


public  **__set** (*unknown* $property, *unknown* $value) inherited from Phalcon\\Di

...


public  **__get** (*unknown* $property) inherited from Phalcon\\Di

...


