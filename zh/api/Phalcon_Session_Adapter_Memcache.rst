Class **Phalcon\\Session\\Adapter\\Memcache**
=============================================

*extends* abstract class :doc:`Phalcon\\Session\\Adapter <Phalcon_Session_Adapter>`

*implements* ArrayAccess, Traversable, IteratorAggregate, Countable, :doc:`Phalcon\\Session\\AdapterInterface <Phalcon_Session_AdapterInterface>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/phalcon/session/adapter/memcache.zep" class="btn btn-default btn-sm">Source on GitHub</a>`

This adapter store sessions in memcache  

.. code-block:: php

    <?php

     $session = new Phalcon\Session\Adapter\Memcache(array(
        'host' => '127.0.0.1',
        'port' => 11211,
        'lifetime' => 3600,
        'persistent' => TRUE,
        'prefix' => 'my_'
     ));
    
     $session->start();
    
     $session->set('var', 'some-value');
    
     echo $session->get('var');



Methods
-------

public  **__construct** (*array* $options)

Constructor for Phalcon\\Session\\Adapter\\Memcache



public *boolean*  **open** ()





public *boolean*  **close** ()





public *mixed*  **read** (*string* $sessionId)





public *boolean*  **write** (*string* $sessionId, *string* $data)





public *boolean*  **destroy** ([*unknown* $sessionId])





public *boolean*  **gc** ()





public  **__destruct** () inherited from Phalcon\\Session\\Adapter

...


public *boolean*  **start** () inherited from Phalcon\\Session\\Adapter

Starts the session (if headers are already sent the session will not be started)



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




