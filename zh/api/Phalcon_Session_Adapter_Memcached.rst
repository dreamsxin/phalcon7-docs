Class **Phalcon\\Session\\Adapter\\Memcached**
==============================================

*extends* abstract class :doc:`Phalcon\\Session\\Adapter <Phalcon_Session_Adapter>`

*implements* ArrayAccess, Traversable, IteratorAggregate, Countable, :doc:`Phalcon\\Session\\AdapterInterface <Phalcon_Session_AdapterInterface>`, :doc:`Phalcon\\Di\\InjectionAwareInterface <Phalcon_Di_InjectionAwareInterface>`, :doc:`Phalcon\\Events\\EventsAwareInterface <Phalcon_Events_EventsAwareInterface>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/session/adapter/memcached.c" class="btn btn-default btn-sm">Source on GitHub</a>`

This adapter store sessions in memcached  

.. code-block:: php

    <?php

     $session = new Phalcon\Session\Adapter\Memcached(array(
         'servers' => array(
             array('host' => 'localhost', 'port' => 11211, 'weight' => 1),
         ),
         'client' => array(
             Memcached::OPT_HASH => Memcached::HASH_MD5,
             Memcached::OPT_PREFIX_KEY => 'prefix.',
         ),
        'lifetime' => 3600,
        'prefix' => 'my_'
     ));
    
     $session->start();
    
     $session->set('var', 'some-value');
    
     echo $session->get('var');



Methods
-------

public *boolean*  **start** ()

Starts the session (if headers are already sent the session will not be started)



public *boolean*  **open** (*unknown* $savePath, *unknown* $sessionName)





public *boolean*  **close** ()





public *mixed*  **read** (*string* $sessionId)





public  **write** (*string* $sessionId, *unknown* $sessionData)





public *boolean*  **destroy** ([*unknown* $regenerate])





public *boolean*  **gc** ([*unknown* $maxlifetime])





public  **__construct** ([*array* $options], [*int* $expire], [*string* $path], [*boolean* $secure], [*string* $domain], [*boolean* $httpOnly]) inherited from Phalcon\\Session\\Adapter

Phalcon\\Session\\Adapter constructor



public  **__destruct** () inherited from Phalcon\\Session\\Adapter

...


public  **setOptions** (*array* $options) inherited from Phalcon\\Session\\Adapter

Sets session's options 

.. code-block:: php

    <?php

    $session->setOptions(array(
    	'uniqueId' => 'my-private-app'
    ));




public *array*  **getOptions** () inherited from Phalcon\\Session\\Adapter

Get internal options



public *mixed*  **get** (*string* $index, [*mixed* $defaultValue]) inherited from Phalcon\\Session\\Adapter

Gets a session variable from an application context



public  **set** (*string* $index, *string* $value) inherited from Phalcon\\Session\\Adapter

Sets a session variable in an application context 

.. code-block:: php

    <?php

    $session->set('auth', 'yes');




public  **sets** (*array* $data) inherited from Phalcon\\Session\\Adapter

Sets a session variables in an application context 

.. code-block:: php

    <?php

    $session->sets(array('auth', 'yes'));




public *boolean*  **has** (*string* $index) inherited from Phalcon\\Session\\Adapter

Check whether a session variable is set in an application context 

.. code-block:: php

    <?php

    var_dump($session->has('auth'));




public  **remove** (*string* $index) inherited from Phalcon\\Session\\Adapter

Removes a session variable from an application context 

.. code-block:: php

    <?php

    $session->remove('auth');




public *string*  **getId** () inherited from Phalcon\\Session\\Adapter

Returns active session id 

.. code-block:: php

    <?php

    echo $session->getId();




public *boolean*  **isStarted** () inherited from Phalcon\\Session\\Adapter

Check whether the session has been started 

.. code-block:: php

    <?php

    var_dump($session->isStarted());




public *boolean*  **regenerate** ([*unknown* $delete_old_session]) inherited from Phalcon\\Session\\Adapter

Update the current session id with a newly generated one  

.. code-block:: php

    <?php

    var_dump($session->regenerate());




public  **__get** (*unknown* $property) inherited from Phalcon\\Session\\Adapter

...


public  **__set** (*unknown* $property, *unknown* $value) inherited from Phalcon\\Session\\Adapter

...


public  **__isset** (*unknown* $property) inherited from Phalcon\\Session\\Adapter

...


public  **__unset** (*unknown* $property) inherited from Phalcon\\Session\\Adapter

...


public  **offsetGet** (*unknown* $property) inherited from Phalcon\\Session\\Adapter

...


public  **offsetSet** (*unknown* $property, *unknown* $value) inherited from Phalcon\\Session\\Adapter

...


public  **offsetExists** (*unknown* $property) inherited from Phalcon\\Session\\Adapter

...


public  **offsetUnset** (*unknown* $property) inherited from Phalcon\\Session\\Adapter

...


public  **count** () inherited from Phalcon\\Session\\Adapter

...


public  **getIterator** () inherited from Phalcon\\Session\\Adapter

...


public  **setId** (*unknown* $sid) inherited from Phalcon\\Session\\Adapter

Set the current session id 

.. code-block:: php

    <?php

    $session->setId($id);




public  **setDI** (:doc:`Phalcon\\DiInterface <Phalcon_DiInterface>` $dependencyInjector) inherited from Phalcon\\Di\\Injectable

Sets the dependency injector



public :doc:`Phalcon\\DiInterface <Phalcon_DiInterface>`  **getDI** ([*unknown* $error], [*unknown* $notUseDefault]) inherited from Phalcon\\Di\\Injectable

Returns the internal dependency injector



public  **setEventsManager** (:doc:`Phalcon\\Events\\ManagerInterface <Phalcon_Events_ManagerInterface>` $eventsManager) inherited from Phalcon\\Di\\Injectable

Sets the event manager



public :doc:`Phalcon\\Events\\ManagerInterface <Phalcon_Events_ManagerInterface>`  **getEventsManager** () inherited from Phalcon\\Di\\Injectable

Returns the internal event manager



public *boolean*  **fireEvent** (*string* $eventName, [*mixed* $data], [*unknown* $cancelable]) inherited from Phalcon\\Di\\Injectable

Fires an event, implicitly calls behaviors and listeners in the events manager are notified



public *mixed*  **fireEventCancel** (*string* $eventName, [*mixed* $data], [*unknown* $cancelable]) inherited from Phalcon\\Di\\Injectable

Fires an event, can stop the event by returning to the false



public *boolean*  **hasService** (*string* $name) inherited from Phalcon\\Di\\Injectable

Check whether the DI contains a service by a name



public :doc:`Phalcon\\Di\\ServiceInterface <Phalcon_Di_ServiceInterface>`  **setService** (*unknown* $name) inherited from Phalcon\\Di\\Injectable

Sets a service from the DI



public *object|null*  **getService** (*unknown* $name) inherited from Phalcon\\Di\\Injectable

Obtains a service from the DI



public *mixed*  **getResolveService** (*string* $name, [*array* $args], [*unknown* $noerror], [*unknown* $noshared]) inherited from Phalcon\\Di\\Injectable

Resolves the service based on its configuration



public  **attachEvent** (*string* $eventType, *Closure* $callback) inherited from Phalcon\\Di\\Injectable

Attach a listener to the events



public  **__sleep** () inherited from Phalcon\\Di\\Injectable

...


public  **__debugInfo** () inherited from Phalcon\\Di\\Injectable

...


