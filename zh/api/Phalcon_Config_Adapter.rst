Abstract class **Phalcon\\Config\\Adapter**
===========================================

*extends* class :doc:`Phalcon\\Config <Phalcon_Config>`

*implements* Countable, ArrayAccess, :doc:`Phalcon\\Config\\AdapterInterface <Phalcon_Config_AdapterInterface>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/config/adapter.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Base class for Phalcon\\Config adapters


Methods
-------

public  **__construct** ([*string* $filePath], [*string* $absolutePath])

Phalcon\\Config\\Adapter constructor



public static  **factory** ([*string* $filePath], [*string* $absolutePath])

Phalcon\\Config\\Adapter factory



public static :doc:`Phalcon\\Config\\Adapter <Phalcon_Config_Adapter>`  **setBasePath** (*string* $basePath)

Sets base path



public static *string*  **getBasePath** ()

Gets base path



public  **load** (*string* $filePath, [*string* $absolutePath], [*unknown* $recursive])

Load a configuration



abstract public  **read** (*unknown* $filePath, [*unknown* $absolutePath])

...


public  **val** (*array* $arrayConfig) inherited from Phalcon\\Config

Sets values



public *boolean*  **offsetExists** (*unknown* $property) inherited from Phalcon\\Config

Allows to check whether an attribute is defined using the array-syntax 

.. code-block:: php

    <?php

     var_dump(isset($config['database']));




public *mixed*  **get** (*string* $index, [*mixed* $defaultValue]) inherited from Phalcon\\Config

Gets an attribute from the configuration, if the attribute isn't defined returns null If the value is exactly null or is not defined the default value will be used instead 

.. code-block:: php

    <?php

     echo $config->get('controllersDir', '../app/controllers/');




public *string*  **offsetGet** (*unknown* $property) inherited from Phalcon\\Config

Gets an attribute using the array-syntax 

.. code-block:: php

    <?php

     print_r($config['database']);




public  **offsetSet** (*unknown* $property, *mixed* $value) inherited from Phalcon\\Config

Sets an attribute using the array-syntax 

.. code-block:: php

    <?php

     $config['database'] = array('type' => 'Sqlite');




public  **offsetUnset** (*unknown* $property) inherited from Phalcon\\Config

Unsets an attribute using the array-syntax 

.. code-block:: php

    <?php

     unset($config['database']);




public :doc:`Phalcon\\Config <Phalcon_Config>`  **merge** (:doc:`Phalcon\\Config <Phalcon_Config>` $config) inherited from Phalcon\\Config

Merges a configuration into the current one 

.. code-block:: php

    <?php

    $appConfig = new Phalcon\Config(array('database' => array('host' => 'localhost')));
    $globalConfig->merge($config2);




public *array*  **toArray** () inherited from Phalcon\\Config

Converts recursively the object to an array 

.. code-block:: php

    <?php

    print_r($config->toArray());




public  **count** () inherited from Phalcon\\Config

...


public static  **setup** (*array* $options) inherited from Phalcon\\Config

...


public  **__wakeup** () inherited from Phalcon\\Config

...


public static :doc:`Phalcon\\Config <Phalcon_Config>`  **__set_state** ([*array* $properties]) inherited from Phalcon\\Config

Restores the state of a Phalcon\\Config object



public  **__get** (*unknown* $property) inherited from Phalcon\\Config

...


public  **__set** (*unknown* $property, *unknown* $value) inherited from Phalcon\\Config

...


public  **__isset** (*unknown* $property) inherited from Phalcon\\Config

...


public  **__unset** (*unknown* $property) inherited from Phalcon\\Config

...


