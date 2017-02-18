Class **Phalcon\\Di**
=====================

*implements* :doc:`Phalcon\\DiInterface <Phalcon_DiInterface>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/di.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Phalcon\\Di is a component that implements Dependency Injection/Service Location of services and it's itself a container for them.  Since Phalcon is highly decoupled, Phalcon\\Di is essential to integrate the different components of the framework. The developer can also use this component to inject dependencies and manage global instances of the different classes used in the application.  Basically, this component implements the `Inversion of Control` pattern. Applying this, the objects do not receive their dependencies using setters or constructors, but requesting a service dependency injector. This reduces the overall complexity, since there is only one way to get the required dependencies within a component.  Additionally, this pattern increases testability in the code, thus making it less prone to errors.  

.. code-block:: php

    <?php

     $di = new Phalcon\Di();
    
     //Using a string definition
     $di->set('request', 'Phalcon\Http\Request', true);
    
     //Using an anonymous function
     $di->set('request', function(){
      return new Phalcon\Http\Request();
     }, true);
    
     $request = $di->getRequest();



Methods
-------

public  **__construct** ([*unknown* $name])

Phalcon\\Di constructor



public *String*  **getName** ()

Returns the name



protected  **setEventsManager** ()

Sets a custom events manager



protected :doc:`Phalcon\\Events\\ManagerInterface <Phalcon_Events_ManagerInterface>`  **getEventsManager** ()

Returns the custom events manager



public :doc:`Phalcon\\Di\\ServiceInterface <Phalcon_Di_ServiceInterface>`  **set** (*string* $name, *mixed* $definition, [*boolean* $shared])

Registers a service in the services container



public  **remove** (*string* $name)

Removes a service in the services container



public :doc:`Phalcon\\Di\\ServiceInterface <Phalcon_Di_ServiceInterface>`  **setRaw** (*string* $name, [*mixed* $definition], [*boolean* $shared])

Returns a service definition without resolving



public *mixed*  **getRaw** (*string* $name)

Returns a service definition without resolving



public :doc:`Phalcon\\Di\\ServiceInterface <Phalcon_Di_ServiceInterface>`  **getService** (*string* $name)

Returns a Phalcon\\Di\\Service instance



public :doc:`Phalcon\\Di\\ServiceInterface <Phalcon_Di_ServiceInterface>`  **setService** (*string* $name, :doc:`Phalcon\\Di\\ServiceInterface <Phalcon_Di_ServiceInterface>` $rawDefinition)

Sets a service using a raw Phalcon\\Di\\Service definition



public *mixed*  **get** (*string* $name, [*array* $parameters], [*boolean* $noError], [*unknown* $noerror])

Resolves the service based on its configuration



public *mixed*  **getShared** (*string* $name, [*array* $parameters], [*boolean* $noError])

Resolves a service, the resolved service is stored in the DI, subsequent requests for this service will return the same instance



public *boolean*  **has** (*string* $name)

Check whether the DI contains a service by a name



public *boolean*  **wasFreshInstance** ()

Check whether the last service obtained via getShared produced a fresh instance or an existing one



public :doc:`Phalcon\\Di\\Service <Phalcon_Di_Service>` [] **getServices** ()

Return the services registered in the DI



public static  **setDefault** (:doc:`Phalcon\\DiInterface <Phalcon_DiInterface>` $dependencyInjector)

Set a default dependency injection container to be obtained into static methods



public static :doc:`Phalcon\\DiInterface <Phalcon_DiInterface>`  **getDefault** ()

Return the lastest DI created



public static  **reset** ()

Resets the internal default DI



public :doc:`Phalcon\\Di\\ServiceInterface <Phalcon_Di_ServiceInterface>`  **attempt** (*string* $name, *mixed* $definition, [*boolean* $shared])

Attempts to register a service in the services container Only is successful if a service hasn't been registered previously with the same name



public :doc:`Phalcon\\Di\\ServiceInterface <Phalcon_Di_ServiceInterface>`  **setShared** (*string* $name, *mixed* $definition)

Registers an "always shared" service in the services container



public *boolean*  **offsetExists** (*unknown* $property)

Check if a service is registered using the array syntax. Alias for Phalcon\\Di::has()



public  **offsetSet** (*unknown* $property, *unknown* $value)

Allows to register a shared service using the array syntax. Alias for Phalcon\\Di::setShared() 

.. code-block:: php

    <?php

    $di['request'] = new Phalcon\Http\Request();




public *mixed*  **offsetGet** (*unknown* $property)

Allows to obtain a shared service using the array syntax. Alias for Phalcon\\Di::getShared() 

.. code-block:: php

    <?php

    var_dump($di['request']);




public  **offsetUnset** (*unknown* $property)

Removes a service from the services container using the array syntax. Alias for Phalcon\\Di::remove()



public *mixed*  **__call** (*string* $method, [*array* $arguments])

Magic method to get or set services using setters/getters



public  **__clone** ()

...


public  **__set** (*unknown* $property, *unknown* $value)

...


public  **__get** (*unknown* $property)

...


