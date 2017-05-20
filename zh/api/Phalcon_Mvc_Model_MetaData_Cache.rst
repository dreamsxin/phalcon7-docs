Class **Phalcon\\Mvc\\Model\\MetaData\\Cache**
==============================================

*extends* abstract class :doc:`Phalcon\\Mvc\\Model\\MetaData <Phalcon_Mvc_Model_MetaData>`

*implements* :doc:`Phalcon\\Mvc\\Model\\MetaDataInterface <Phalcon_Mvc_Model_MetaDataInterface>`, :doc:`Phalcon\\Di\\InjectionAwareInterface <Phalcon_Di_InjectionAwareInterface>`, :doc:`Phalcon\\Events\\EventsAwareInterface <Phalcon_Events_EventsAwareInterface>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/mvc/model/metadata/cache.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Stores model meta-data in the Cache cache. Data will erased if the web server is restarted  By default meta-data is stored for 48 hours (172800 seconds)  You can query the meta-data by printing cache_get('$PMM$') or cache_get('$PMM$my-app-id')  

.. code-block:: php

    <?php

    $metaData = new Phalcon\Mvc\Model\Metadata\Cache(array(
    	'service' => 'cache', // Service Name
    	'lifetime' => 86400,
    ));



Constants
---------

*integer* **MODELS_ATTRIBUTES**

*integer* **MODELS_PRIMARY_KEY**

*integer* **MODELS_NON_PRIMARY_KEY**

*integer* **MODELS_NOT_NULL**

*integer* **MODELS_DATA_TYPES**

*integer* **MODELS_DATA_TYPES_NUMERIC**

*integer* **MODELS_DATE_AT**

*integer* **MODELS_DATE_IN**

*integer* **MODELS_IDENTITY_COLUMN**

*integer* **MODELS_DATA_TYPES_BIND**

*integer* **MODELS_AUTOMATIC_DEFAULT_INSERT**

*integer* **MODELS_AUTOMATIC_DEFAULT_UPDATE**

*integer* **MODELS_DATA_DEFAULT_VALUE**

*integer* **MODELS_DATA_SZIE**

*integer* **MODELS_DATA_SCALE**

*integer* **MODELS_DATA_BYTE**

*integer* **MODELS_COLUMN_MAP**

*integer* **MODELS_REVERSE_COLUMN_MAP**

Methods
-------

public  **__construct** ([*array* $options])

Phalcon\\Mvc\\Model\\MetaData\\Cache constructor



protected  **_getCache** ()

...


public *array*  **read** (*string* $key)

Reads metadata from Cache



public  **write** (*string* $key, *array* $data)

Writes the metadata to Cache



public  **reset** ()

...


protected  **_initialize** () inherited from Phalcon\\Mvc\\Model\\MetaData

Initialize the metadata for certain table



public  **setStrategy** (:doc:`Phalcon\\Mvc\\Model\\MetaData\\Strategy\\Introspection <Phalcon_Mvc_Model_MetaData_Strategy_Introspection>` $strategy) inherited from Phalcon\\Mvc\\Model\\MetaData

Set the meta-data extraction strategy



public :doc:`Phalcon\\Mvc\\Model\\MetaData\\Strategy\\Introspection <Phalcon_Mvc_Model_MetaData_Strategy_Introspection>`  **getStrategy** () inherited from Phalcon\\Mvc\\Model\\MetaData

Return the strategy to obtain the meta-data



public *array*  **readMetaData** (:doc:`Phalcon\\Mvc\\ModelInterface <Phalcon_Mvc_ModelInterface>` $model) inherited from Phalcon\\Mvc\\Model\\MetaData

Reads the complete meta-data for certain model 

.. code-block:: php

    <?php

    print_r($metaData->readMetaData(new Robots()));




public *array*  **readMetaDataIndex** (:doc:`Phalcon\\Mvc\\ModelInterface <Phalcon_Mvc_ModelInterface>` $model, *int* $index) inherited from Phalcon\\Mvc\\Model\\MetaData

Reads meta-data for certain model 

.. code-block:: php

    <?php

    print_r($metaData->readMetaDataIndex(new Robots(), 0);




public  **writeMetaDataIndex** (:doc:`Phalcon\\Mvc\\ModelInterface <Phalcon_Mvc_ModelInterface>` $model, *int* $index, *mixed* $data, *unknown* $replace) inherited from Phalcon\\Mvc\\Model\\MetaData

Writes meta-data for certain model using a MODEL_* constant 

.. code-block:: php

    <?php

    print_r($metaData->writeColumnMapIndex(new Robots(), MetaData::MODELS_REVERSE_COLUMN_MAP, array('leName' => 'name')));




public *array*  **readColumnMap** (:doc:`Phalcon\\Mvc\\ModelInterface <Phalcon_Mvc_ModelInterface>` $model) inherited from Phalcon\\Mvc\\Model\\MetaData

Reads the ordered/reversed column map for certain model 

.. code-block:: php

    <?php

    print_r($metaData->readColumnMap(new Robots()));




public  **readColumnMapIndex** (:doc:`Phalcon\\Mvc\\ModelInterface <Phalcon_Mvc_ModelInterface>` $model, *int* $index) inherited from Phalcon\\Mvc\\Model\\MetaData

Reads column-map information for certain model using a MODEL_* constant 

.. code-block:: php

    <?php

    print_r($metaData->readColumnMapIndex(new Robots(), MetaData::MODELS_REVERSE_COLUMN_MAP));




public *array*  **getAttributes** (:doc:`Phalcon\\Mvc\\ModelInterface <Phalcon_Mvc_ModelInterface>` $model) inherited from Phalcon\\Mvc\\Model\\MetaData

Returns table attributes names (fields) 

.. code-block:: php

    <?php

    print_r($metaData->getAttributes(new Robots()));




public *array*  **getPrimaryKeyAttributes** (:doc:`Phalcon\\Mvc\\ModelInterface <Phalcon_Mvc_ModelInterface>` $model) inherited from Phalcon\\Mvc\\Model\\MetaData

Returns an array of fields which are part of the primary key 

.. code-block:: php

    <?php

    print_r($metaData->getPrimaryKeyAttributes(new Robots()));




public *array*  **getNonPrimaryKeyAttributes** (:doc:`Phalcon\\Mvc\\ModelInterface <Phalcon_Mvc_ModelInterface>` $model) inherited from Phalcon\\Mvc\\Model\\MetaData

Returns an arrau of fields which are not part of the primary key 

.. code-block:: php

    <?php

    print_r($metaData->getNonPrimaryKeyAttributes(new Robots()));




public *array*  **getNotNullAttributes** (:doc:`Phalcon\\Mvc\\ModelInterface <Phalcon_Mvc_ModelInterface>` $model) inherited from Phalcon\\Mvc\\Model\\MetaData

Returns an array of not null attributes 

.. code-block:: php

    <?php

    print_r($metaData->getNotNullAttributes(new Robots()));




public *boolean*  **isNotNull** (:doc:`Phalcon\\Mvc\\ModelInterface <Phalcon_Mvc_ModelInterface>` $model, *string* $attribute) inherited from Phalcon\\Mvc\\Model\\MetaData

Checks if the attribute is not null 

.. code-block:: php

    <?php

    var_dump($metaData->isNotNull(new Robots(), 'type');




public *array*  **getDataTypes** (:doc:`Phalcon\\Mvc\\ModelInterface <Phalcon_Mvc_ModelInterface>` $model) inherited from Phalcon\\Mvc\\Model\\MetaData

Returns attributes and their data types 

.. code-block:: php

    <?php

    print_r($metaData->getDataTypes(new Robots()));




public *int*  **getDataType** (:doc:`Phalcon\\Mvc\\ModelInterface <Phalcon_Mvc_ModelInterface>` $model, *string* $attribute) inherited from Phalcon\\Mvc\\Model\\MetaData

Returns attribute data type 

.. code-block:: php

    <?php

    print_r($metaData->getDataType(new Robots(), 'type'));




public *array*  **getDataSizes** (:doc:`Phalcon\\Mvc\\ModelInterface <Phalcon_Mvc_ModelInterface>` $model) inherited from Phalcon\\Mvc\\Model\\MetaData

Returns attributes and their data sizes 

.. code-block:: php

    <?php

    print_r($metaData->getDataSizes(new Robots()));




public *int*  **getDataSize** (:doc:`Phalcon\\Mvc\\ModelInterface <Phalcon_Mvc_ModelInterface>` $model, *string* $attribute) inherited from Phalcon\\Mvc\\Model\\MetaData

Returns attribute data size 

.. code-block:: php

    <?php

    print_r($metaData->getDataSize(new Robots(), 'type'));




public *int*  **getDataBytes** (:doc:`Phalcon\\Mvc\\ModelInterface <Phalcon_Mvc_ModelInterface>` $model) inherited from Phalcon\\Mvc\\Model\\MetaData

Returns attributes and their data bytes 

.. code-block:: php

    <?php

    print_r($metaData->getDataBytes(new Robots()));




public *int*  **getDataByte** (:doc:`Phalcon\\Mvc\\ModelInterface <Phalcon_Mvc_ModelInterface>` $model, *string* $attribute) inherited from Phalcon\\Mvc\\Model\\MetaData

Returns attribute data byte 

.. code-block:: php

    <?php

    print_r($metaData->getDataByte(new Robots(), 'type'));




public *array*  **getDataScales** (:doc:`Phalcon\\Mvc\\ModelInterface <Phalcon_Mvc_ModelInterface>` $model) inherited from Phalcon\\Mvc\\Model\\MetaData

Returns attributes and their data scales 

.. code-block:: php

    <?php

    print_r($metaData->getDataScales(new Robots()));




public *int*  **getDataScale** (:doc:`Phalcon\\Mvc\\ModelInterface <Phalcon_Mvc_ModelInterface>` $model, *string* $attribute) inherited from Phalcon\\Mvc\\Model\\MetaData

Returns attribute data scale 

.. code-block:: php

    <?php

    print_r($metaData->getDataScale(new Robots(), 'type'));




public *array*  **getDataTypesNumeric** (:doc:`Phalcon\\Mvc\\ModelInterface <Phalcon_Mvc_ModelInterface>` $model) inherited from Phalcon\\Mvc\\Model\\MetaData

Returns attributes which types are numerical 

.. code-block:: php

    <?php

    print_r($metaData->getDataTypesNumeric(new Robots()));




public *int*  **isNumeric** (:doc:`Phalcon\\Mvc\\ModelInterface <Phalcon_Mvc_ModelInterface>` $model, *string* $attribute) inherited from Phalcon\\Mvc\\Model\\MetaData

Checks if the attribute is numerical 

.. code-block:: php

    <?php

    var_dump($metaData->isNumeric(new Robots(), 'id'));




public *string*  **getIdentityField** (:doc:`Phalcon\\Mvc\\ModelInterface <Phalcon_Mvc_ModelInterface>` $model) inherited from Phalcon\\Mvc\\Model\\MetaData

Returns the name of identity field (if one is present) 

.. code-block:: php

    <?php

    print_r($metaData->getIdentityField(new Robots()));




public *array*  **getBindTypes** (:doc:`Phalcon\\Mvc\\ModelInterface <Phalcon_Mvc_ModelInterface>` $model) inherited from Phalcon\\Mvc\\Model\\MetaData

Returns attributes and their bind data types 

.. code-block:: php

    <?php

    print_r($metaData->getBindTypes(new Robots()));




public *array*  **getDefaultValues** (:doc:`Phalcon\\Mvc\\ModelInterface <Phalcon_Mvc_ModelInterface>` $model) inherited from Phalcon\\Mvc\\Model\\MetaData

Returns attributes and their default values 

.. code-block:: php

    <?php

    print_r($metaData->getDefaultValues(new Robots()));




public *array*  **getAutomaticCreateAttributes** (:doc:`Phalcon\\Mvc\\ModelInterface <Phalcon_Mvc_ModelInterface>` $model) inherited from Phalcon\\Mvc\\Model\\MetaData

Returns attributes that must be ignored from the INSERT SQL generation 

.. code-block:: php

    <?php

    print_r($metaData->getAutomaticCreateAttributes(new Robots()));




public *array*  **getAutomaticUpdateAttributes** (:doc:`Phalcon\\Mvc\\ModelInterface <Phalcon_Mvc_ModelInterface>` $model) inherited from Phalcon\\Mvc\\Model\\MetaData

Returns attributes that must be ignored from the UPDATE SQL generation 

.. code-block:: php

    <?php

    print_r($metaData->getAutomaticUpdateAttributes(new Robots()));




public  **setAutomaticCreateAttributes** (:doc:`Phalcon\\Mvc\\ModelInterface <Phalcon_Mvc_ModelInterface>` $model, *array* $attributes, *unknown* $replace) inherited from Phalcon\\Mvc\\Model\\MetaData

Set the attributes that must be ignored from the INSERT SQL generation 

.. code-block:: php

    <?php

    $metaData->setAutomaticCreateAttributes(new Robots(), array('created_at' => true));




public  **setAutomaticUpdateAttributes** (:doc:`Phalcon\\Mvc\\ModelInterface <Phalcon_Mvc_ModelInterface>` $model, *array* $attributes, *unknown* $replace) inherited from Phalcon\\Mvc\\Model\\MetaData

Set the attributes that must be ignored from the UPDATE SQL generation 

.. code-block:: php

    <?php

    $metaData->setAutomaticUpdateAttributes(new Robots(), array('modified_at' => true));




public *array*  **getColumnMap** (:doc:`Phalcon\\Mvc\\ModelInterface <Phalcon_Mvc_ModelInterface>` $model) inherited from Phalcon\\Mvc\\Model\\MetaData

Returns the column map if any 

.. code-block:: php

    <?php

    print_r($metaData->getColumnMap(new Robots()));




public *array*  **getReverseColumnMap** (:doc:`Phalcon\\Mvc\\ModelInterface <Phalcon_Mvc_ModelInterface>` $model) inherited from Phalcon\\Mvc\\Model\\MetaData

Returns the reverse column map if any 

.. code-block:: php

    <?php

    print_r($metaData->getReverseColumnMap(new Robots()));




public *boolean*  **hasAttribute** (:doc:`Phalcon\\Mvc\\ModelInterface <Phalcon_Mvc_ModelInterface>` $model, *string* $attribute) inherited from Phalcon\\Mvc\\Model\\MetaData

Check if a model has certain attribute 

.. code-block:: php

    <?php

    var_dump($metaData->hasAttribute(new Robots(), 'name'));




public *string*  **getAttribute** (:doc:`Phalcon\\Mvc\\ModelInterface <Phalcon_Mvc_ModelInterface>` $model, *unknown* $attribute) inherited from Phalcon\\Mvc\\Model\\MetaData

Gets a model certain attribute 

.. code-block:: php

    <?php

    var_dump($metaData->getAttribute(new Robots(), 'name'));




public *boolean*  **hasRealAttribute** (:doc:`Phalcon\\Mvc\\ModelInterface <Phalcon_Mvc_ModelInterface>` $model, *string* $column) inherited from Phalcon\\Mvc\\Model\\MetaData

Check if a model has real attribute name 

.. code-block:: php

    <?php

    var_dump($metaData->hasRealAttribute(new Robots(), 'name'));




public *string*  **getRealAttribute** (:doc:`Phalcon\\Mvc\\ModelInterface <Phalcon_Mvc_ModelInterface>` $model, *string* $column) inherited from Phalcon\\Mvc\\Model\\MetaData

Gets a real attribute name 

.. code-block:: php

    <?php

    var_dump($metaData->getRealAttribute(new Robots(), 'name'));




public *boolean*  **isEmpty** () inherited from Phalcon\\Mvc\\Model\\MetaData

Checks if the internal meta-data container is empty 

.. code-block:: php

    <?php

    var_dump($metaData->isEmpty());




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


