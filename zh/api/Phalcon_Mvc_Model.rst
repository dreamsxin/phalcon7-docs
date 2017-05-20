Abstract class **Phalcon\\Mvc\\Model**
======================================

*extends* abstract class :doc:`Phalcon\\Di\\Injectable <Phalcon_Di_Injectable>`

*implements* :doc:`Phalcon\\Events\\EventsAwareInterface <Phalcon_Events_EventsAwareInterface>`, :doc:`Phalcon\\Di\\InjectionAwareInterface <Phalcon_Di_InjectionAwareInterface>`, :doc:`Phalcon\\Mvc\\ModelInterface <Phalcon_Mvc_ModelInterface>`, :doc:`Phalcon\\Mvc\\Model\\ResultInterface <Phalcon_Mvc_Model_ResultInterface>`, Serializable, JsonSerializable

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/mvc/model.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Phalcon\\Mvc\\Model connects business objects and database tables to create a persistable domain model where logic and data are presented in one wrapping. It‘s an implementation of the object-relational mapping (ORM).    A model represents the information (data) of the application and the rules to manipulate that data. Models are primarily used for managing the rules of interaction with a corresponding database table. In most cases, each table in your database will correspond to one model in your application. The bulk of your application’s business logic will be concentrated in the models.    Phalcon\\Mvc\\Model is the first ORM written in C-language for PHP, giving to developers high performance when interacting with databases while is also easy to use.    

.. code-block:: php

    <?php

     $robot = new Robots();
     $robot->type = 'mechanical';
     $robot->name = 'Astro Boy';
     $robot->year = 1952;
     if ($robot->save() == false) {
      echo "Umh, We can store robots: ";
      foreach ($robot->getMessages() as $message) {
        echo $message;
      }
     } else {
      echo "Great, a new robot was saved successfully!";
     }



Constants
---------

*integer* **OP_NONE**

*integer* **OP_CREATE**

*integer* **OP_UPDATE**

*integer* **OP_DELETE**

*integer* **DIRTY_STATE_PERSISTENT**

*integer* **DIRTY_STATE_TRANSIENT**

*integer* **DIRTY_STATE_DETACHED**

Methods
-------

final public  **__construct** ([*unknown* $data], [:doc:`Phalcon\\DiInterface <Phalcon_DiInterface>` $dependencyInjector])

Phalcon\\Mvc\\Model constructor



public  **setEventsManager** (:doc:`Phalcon\\Events\\ManagerInterface <Phalcon_Events_ManagerInterface>` $eventsManager)

Sets a custom events manager



public :doc:`Phalcon\\Events\\ManagerInterface <Phalcon_Events_ManagerInterface>`  **getEventsManager** ()

Returns the custom events manager



public :doc:`Phalcon\\Mvc\\Model\\MetaDataInterface <Phalcon_Mvc_Model_MetaDataInterface>`  **getModelsMetaData** ()

Returns the models meta-data service related to the entity instance



public :doc:`Phalcon\\Mvc\\Model\\ManagerInterface <Phalcon_Mvc_Model_ManagerInterface>`  **getModelsManager** ()

Returns the models manager related to the entity instance



public :doc:`Phalcon\\Mvc\\Model <Phalcon_Mvc_Model>`  **setTransaction** (:doc:`Phalcon\\Mvc\\Model\\TransactionInterface <Phalcon_Mvc_Model_TransactionInterface>` $transaction)

Sets a transaction related to the Model instance 

.. code-block:: php

    <?php

    use Phalcon\Mvc\Model\Transaction\Manager as TxManager;
    use Phalcon\Mvc\Model\Transaction\Failed as TxFailed;
    
    try {
    
      $txManager = new TxManager();
    
      $transaction = $txManager->get();
    
      $robot = new Robots();
      $robot->setTransaction($transaction);
      $robot->name = 'WALL·E';
      $robot->created_at = date('Y-m-d');
      if ($robot->save() == false) {
        $transaction->rollback("Can't save robot");
      }
    
      $robotPart = new RobotParts();
      $robotPart->setTransaction($transaction);
      $robotPart->type = 'head';
      if ($robotPart->save() == false) {
        $transaction->rollback("Robot part cannot be saved");
      }
    
      $transaction->commit();
    
    } catch (TxFailed $e) {
      echo 'Failed, reason: ', $e->getMessage();
    }




public :doc:`Phalcon\\Mvc\\Model\\TransactionInterface <Phalcon_Mvc_Model_TransactionInterface>`  **getTransaction** ()

Returns a transaction related in the Model instance



protected :doc:`Phalcon\\Mvc\\Model <Phalcon_Mvc_Model>`  **setSource** (*string* $source)

Sets table name which model should be mapped



public *string*  **getSource** ()

Returns table name mapped in the model



protected :doc:`Phalcon\\Mvc\\Model <Phalcon_Mvc_Model>`  **setSchema** (*string* $schema)

Sets schema name where table mapped is located



public *string*  **getSchema** ()

Returns schema name where table mapped is located



public *string*  **getIdentityField** ()

Returns the name of identity field (if one is present)



public *array*  **getColumnMap** ()

Returns the column map if any



public *array*  **getReverseColumnMap** ()

Returns the reverse column map if any



public *array*  **getAttributes** ()

Returns table attributes names (fields)



public *array*  **getPrimaryKeyAttributes** ()

Returns an array of fields which are part of the primary key



public *array*  **getNonPrimaryKeyAttributes** ()

Returns an arrau of fields which are not part of the primary key



public *array*  **getNotNullAttributes** ()

Returns an array of not null attributes



public *array*  **getDataTypesNumeric** ()

Returns attributes which types are numerical



public *array*  **isNotNull** (*unknown* $attribute)

Checks if the attribute is not null



public *array*  **getDataTypes** ()

Returns the columns data types



public *array*  **getDataSize** (*string* $attribute)

Returns attribute data size



public *array*  **getDataByte** (*string* $attribute)

Returns attribute data byte



public *array*  **getDataScale** (*string* $attribute)

Returns attribute data scale



public *array*  **getBindTypes** ()

Returns attributes and their bind data types



public *array*  **getDefaultValues** ()

Returns attributes and their default values



public *array*  **getAutomaticCreateAttributes** ()

Returns attributes that must be ignored from the INSERT SQL generation



public *array*  **getAutomaticUpdateAttributes** ()

Returns attributes that must be ignored from the UPDATE SQL generation



public *boolean*  **hasRealAttribute** (*string* $column)

Check if a model has certain column



public *string*  **getRealAttribute** (*string* $column)

Gets a model certain column



public *boolean*  **hasAttribute** (*string* $attribute)

Check if a model has certain attribute



public *string*  **getAttribute** (*string* $attribute)

Gets a model certain attribute



public :doc:`Phalcon\\Mvc\\Model <Phalcon_Mvc_Model>`  **setConnectionService** (*string* $connectionService)

Sets the DependencyInjection connection service name



public :doc:`Phalcon\\Mvc\\Model <Phalcon_Mvc_Model>`  **setReadConnectionService** (*string* $connectionService)

Sets the DependencyInjection connection service name used to read data



public :doc:`Phalcon\\Mvc\\Model <Phalcon_Mvc_Model>`  **setWriteConnectionService** (*string* $connectionService)

Sets the DependencyInjection connection service name used to write data



public *string*  **getReadConnectionService** ()

Returns the DependencyInjection connection service name used to read data related the model



public *string*  **getWriteConnectionService** ()

Returns the DependencyInjection connection service name used to write data related to the model



public :doc:`Phalcon\\Mvc\\Model <Phalcon_Mvc_Model>`  **setDirtyState** (*int* $dirtyState)

Sets the dirty state of the object using one of the DIRTY_STATE_* constants



public *int*  **getDirtyState** ()

Returns one of the DIRTY_STATE_* constants telling if the record exists in the database or not



public :doc:`Phalcon\\Db\\AdapterInterface <Phalcon_Db_AdapterInterface>`  **getReadConnection** ()

Gets the connection used to read data for the model



public :doc:`Phalcon\\Db\\AdapterInterface <Phalcon_Db_AdapterInterface>`  **getWriteConnection** ()

Gets the connection used to write data to the model



public :doc:`Phalcon\\Mvc\\Model <Phalcon_Mvc_Model>`  **assign** (*array* $data, [*array* $columnMap], [*array* $whiteList], [*unknown* $negate])

Assigns values to a model from an array 

.. code-block:: php

    <?php

    $robot->assign(array(
      'type' => 'mechanical',
      'name' => 'Astro Boy',
      'year' => 1952
    ));




public static :doc:`Phalcon\\Mvc\\Model <Phalcon_Mvc_Model>`  **cloneResultMap** (:doc:`Phalcon\\Mvc\\Model <Phalcon_Mvc_Model>` $base, *array* $data, *array* $columnMap, *int* $dirtyState, [*boolean* $keepSnapshots], [:doc:`Phalcon\\Mvc\\Model <Phalcon_Mvc_Model>` $sourceModel])

Assigns values to a model from an array returning a new model. 

.. code-block:: php

    <?php

    $robot = \Phalcon\Mvc\Model::cloneResultMap(new Robots(), array(
      'type' => 'mechanical',
      'name' => 'Astro Boy',
      'year' => 1952
    ));




public static *mixed*  **cloneResultMapHydrate** (*array* $data, *array* $columnMap, *int* $hydrationMode, [:doc:`Phalcon\\Mvc\\Model <Phalcon_Mvc_Model>` $sourceModel])

Returns an hydrated result based on the data and the column map



public static :doc:`Phalcon\\Mvc\\Model <Phalcon_Mvc_Model>`  **cloneResult** (:doc:`Phalcon\\Mvc\\Model <Phalcon_Mvc_Model>` $base, *array* $data, [*int* $dirtyState], [*unknown* $sourceModel])

Assigns values to a model from an array returning a new model 

.. code-block:: php

    <?php

    $robot = Phalcon\Mvc\Model::cloneResult(new Robots(), array(
      'type' => 'mechanical',
      'name' => 'Astro Boy',
      'year' => 1952
    ));




public static :doc:`Phalcon\\Mvc\\Model\\ResultsetInterface <Phalcon_Mvc_Model_ResultsetInterface>`  **find** ([*array* $parameters])

Allows to query a set of records that match the specified conditions 

.. code-block:: php

    <?php

     //How many robots are there?
     $robots = Robots::find();
     echo "There are ", count($robots), "\n";
    
     //How many mechanical robots are there?
     $robots = Robots::find("type='mechanical'");
     echo "There are ", count($robots), "\n";
    
     //Get and print virtual robots ordered by name
     $robots = Robots::find(array("type='virtual'", "order" => "name"));
     foreach ($robots as $robot) {
       echo $robot->name, "\n";
     }
    
     //Get first 100 virtual robots ordered by name
     $robots = Robots::find(array("type='virtual'", "order" => "name", "limit" => 100));
     foreach ($robots as $robot) {
       echo $robot->name, "\n";
     }




public static :doc:`Phalcon\\Mvc\\Model <Phalcon_Mvc_Model>`  **findFirst** ([*array* $parameters], [*bool* $autoCreate])

Allows to query the first record that match the specified conditions 

.. code-block:: php

    <?php

     //What's the first robot in robots table?
     $robot = Robots::findFirst();
     echo "The robot name is ", $robot->name;
    
     //What's the first mechanical robot in robots table?
     $robot = Robots::findFirst("type='mechanical'");
     echo "The first mechanical robot name is ", $robot->name;
    
     //Get first virtual robot ordered by name
     $robot = Robots::findFirst(array("type='virtual'", "order" => "name"));
     echo "The first virtual robot name is ", $robot->name;




public static :doc:`Phalcon\\Mvc\\Model\\Criteria <Phalcon_Mvc_Model_Criteria>`  **query** ([:doc:`Phalcon\\DiInterface <Phalcon_DiInterface>` $dependencyInjector])

Create a criteria for a specific model



public *boolean*  **build** ()

Builds a unique primary key condition



public *string*  **getUniqueKey** ()

Gets a unique key



public *array*  **getUniqueParams** ()

Gets a unique params



public *array*  **getUniqueTypes** ()

Gets a unique params



protected *boolean*  **_reBuild** ()

Builds a unique primary key condition



protected *boolean*  **_exists** ()

Checks if the current record already exists or not



protected static :doc:`Phalcon\\Mvc\\Model\\ResultsetInterface <Phalcon_Mvc_Model_ResultsetInterface>`  **_groupResult** ()

Generate a PHQL SELECT statement for an aggregate



public static *int*  **count** ([*array* $parameters])

Allows to count how many records match the specified conditions 

.. code-block:: php

    <?php

     //How many robots are there?
     $number = Robots::count();
     echo "There are ", $number, "\n";
    
     //How many mechanical robots are there?
     $number = Robots::count("type='mechanical'");
     echo "There are ", $number, " mechanical robots\n";




public static *double*  **sum** ([*array* $parameters])

Allows to calculate a summatory on a column that match the specified conditions 

.. code-block:: php

    <?php

     //How much are all robots?
     $sum = Robots::sum(array('column' => 'price'));
     echo "The total price of robots is ", $sum, "\n";
    
     //How much are mechanical robots?
     $sum = Robots::sum(array("type='mechanical'", 'column' => 'price'));
     echo "The total price of mechanical robots is  ", $sum, "\n";




public static *mixed*  **maximum** ([*array* $parameters])

Allows to get the maximum value of a column that match the specified conditions 

.. code-block:: php

    <?php

     //What is the maximum robot id?
     $id = Robots::maximum(array('column' => 'id'));
     echo "The maximum robot id is: ", $id, "\n";
    
     //What is the maximum id of mechanical robots?
     $sum = Robots::maximum(array("type='mechanical'", 'column' => 'id'));
     echo "The maximum robot id of mechanical robots is ", $id, "\n";




public static *mixed*  **minimum** ([*array* $parameters])

Allows to get the minimum value of a column that match the specified conditions 

.. code-block:: php

    <?php

     //What is the minimum robot id?
     $id = Robots::minimum(array('column' => 'id'));
     echo "The minimum robot id is: ", $id;
    
     //What is the minimum id of mechanical robots?
     $sum = Robots::minimum(array("type='mechanical'", 'column' => 'id'));
     echo "The minimum robot id of mechanical robots is ", $id;




public static *double*  **average** ([*array* $parameters])

Allows to calculate the average value on a column matching the specified conditions 

.. code-block:: php

    <?php

     //What's the average price of robots?
     $average = Robots::average(array('column' => 'price'));
     echo "The average price is ", $average, "\n";
    
     //What's the average price of mechanical robots?
     $average = Robots::average(array("type='mechanical'", 'column' => 'price'));
     echo "The average price of mechanical robots is ", $average, "\n";




public *boolean*  **fireEvent** (*string* $eventName, [*unknown* $data], [*unknown* $cancelable])

Fires an event, implicitly calls behaviors and listeners in the events manager are notified



public *boolean*  **fireEventCancel** (*string* $eventName, [*unknown* $data], [*unknown* $cancelable])

Fires an event, implicitly calls behaviors and listeners in the events manager are notified This method stops if one of the callbacks/listeners returns boolean false



protected *boolean*  **_cancelOperation** ()

Cancel the current operation



public :doc:`Phalcon\\Mvc\\Model <Phalcon_Mvc_Model>`  **appendMessage** (:doc:`Phalcon\\Validation\\MessageInterface <Phalcon_Validation_MessageInterface>` $message, [*unknown* $field], [*unknown* $type], [*unknown* $code])

Appends a customized message on the validation process 

.. code-block:: php

    <?php

     use \Phalcon\Validation\Message as Message;
    
     class Robots extends Phalcon\Mvc\Model
     {
    
       public function beforeSave()
       {
         if ($this->name == 'Peter') {
            $message = new Message("Sorry, but a robot cannot be named Peter");
            $this->appendMessage($message);
         }
       }
     }




protected :doc:`Phalcon\\Mvc\\Model <Phalcon_Mvc_Model>`  **validate** (*array|Phalcon\\ValidationInterface* $validation)

Executes validators on every validation call 

.. code-block:: php

    <?php

    use Phalcon\Mvc\Model\Validator\ExclusionIn as ExclusionIn;
    
    class Subscriptors extends Phalcon\Mvc\Model
    {
    
    public function validation()
      {
     		$validation = new Phalcon\Validation();
     		$validation->add('status', new ExclusionIn(array(
    		'domain' => array('A', 'I')
    	)));
     		return $this->validate($validation);
    }
    
    }




public *boolean*  **validationHasFailed** ()

Check whether validation process has generated any messages 

.. code-block:: php

    <?php

    use Phalcon\Mvc\Model\Validator\ExclusionIn as ExclusionIn;
    
    class Subscriptors extends Phalcon\Mvc\Model
    {
    
    public function validation()
      {
     		$this->validate(new ExclusionIn(array(
    		'field' => 'status',
    		'domain' => array('A', 'I')
    	)));
    	if ($this->validationHasFailed() == true) {
    		return false;
    	}
    }
    
    }




public *Phalcon\\Mvc\\Model\\MessageInterface[]*  **getMessages** ([*unknown* $filter])

Returns all the validation messages 

.. code-block:: php

    <?php

    $robot = new Robots();
    $robot->type = 'mechanical';
    $robot->name = 'Astro Boy';
    $robot->year = 1952;
    if ($robot->save() == false) {
      	echo "Umh, We can't store robots right now ";
      	foreach ($robot->getMessages() as $message) {
    		echo $message;
    	}
    } else {
      	echo "Great, a new robot was saved successfully!";
    }




protected *boolean*  **_checkForeignKeysRestrict** ()

Reads "belongs to" relations and check the virtual foreign keys when inserting or updating records to verify that inserted/updated values are present in the related entity



protected *boolean*  **_checkForeignKeysReverseRestrict** ()

Reads both "hasMany" and "hasOne" relations and checks the virtual foreign keys (restrict) when deleting records



protected *boolean*  **_checkForeignKeysReverseCascade** ()

Reads both "hasMany" and "hasOne" relations and checks the virtual foreign keys (cascade) when deleting records



protected *boolean*  **_preSave** ()

Executes internal hooks before save a record



protected *boolean*  **_postSave** ()

Executes internal events after save a record



protected *boolean*  **_doLowInsert** ()

Sends a pre-build INSERT SQL statement to the relational database system



protected *boolean*  **_doLowUpdate** ()

Sends a pre-build UPDATE SQL statement to the relational database system



protected *boolean*  **_preSaveRelatedRecords** ()

Saves related records that must be stored prior to save the master record



protected *boolean*  **_postSaveRelatedRecords** ()

Save the related records assigned in the has-one/has-many relations



public *boolean*  **save** ([*array* $data], [*array* $whiteList], [*array* $exists])

Inserts or updates a model instance. Returning true on success or false otherwise. 

.. code-block:: php

    <?php

    //Creating a new robot
    $robot = new Robots();
    $robot->type = 'mechanical';
    $robot->name = 'Astro Boy';
    $robot->year = 1952;
    $robot->save();
    
    //Updating a robot name
    $robot = Robots::findFirst("id=100");
    $robot->name = "Biomass";
    $robot->save();




public *boolean*  **create** ([*array* $data], [*array* $whiteList], [*boolean* $existsCheck])

Inserts a model instance. If the instance already exists in the persistance it will throw an exception Returning true on success or false otherwise. 

.. code-block:: php

    <?php

    //Creating a new robot
    $robot = new Robots();
    $robot->type = 'mechanical';
    $robot->name = 'Astro Boy';
    $robot->year = 1952;
    $robot->create();
    
      //Passing an array to create
      $robot = new Robots();
      $robot->create(array(
          'type' => 'mechanical',
          'name' => 'Astroy Boy',
          'year' => 1952
      ));




public *boolean*  **update** ([*array* $data], [*array* $whiteList], [*boolean* $existsCheck])

Updates a model instance. If the instance doesn't exist in the persistance it will throw an exception Returning true on success or false otherwise. 

.. code-block:: php

    <?php

    //Updating a robot name
    $robot = Robots::findFirst("id=100");
    $robot->name = "Biomass";
    $robot->update();




public *boolean*  **delete** ()

Deletes a model instance. Returning true on success or false otherwise. 

.. code-block:: php

    <?php

    $robot = Robots::findFirst("id=100");
    $robot->delete();
    
    foreach (Robots::find("type = 'mechanical'") as $robot) {
       $robot->delete();
    }




public *int*  **getOperationMade** ()

Returns the type of the latest operation performed by the ORM Returns one of the OP_* class constants



public  **refresh** ()

Refreshes the model attributes re-querying the record from the database



public  **skipOperation** (*boolean* $skip)

Skips the current operation forcing a success state



public *mixed*  **readAttribute** (*string* $attribute)

Reads an attribute value by its name 

.. code-block:: php

    <?php

     echo $robot->readAttribute('name');




public  **writeAttribute** (*string* $attribute, *mixed* $value)

Writes an attribute value by its name 

.. code-block:: php

    <?php

     	$robot->writeAttribute('name', 'Rosey');




protected  **skipAttributes** (*array* $attributes, [*boolean* $replace])

Sets a list of attributes that must be skipped from the generated INSERT/UPDATE statement 

.. code-block:: php

    <?php

    class Robots extends \Phalcon\Mvc\Model
    {
    
       public function initialize()
       {
           $this->skipAttributes(array('price'));
       }
    
    }




protected  **skipAttributesOnCreate** (*array* $attributes, [*boolean* $replace])

Sets a list of attributes that must be skipped from the generated INSERT statement 

.. code-block:: php

    <?php

    class Robots extends \Phalcon\Mvc\Model
    {
    
       public function initialize()
       {
           $this->skipAttributesOnCreate(array('created_at'));
       }
    
    }




public *array*  **getSkipAttributesOnCreate** ()

Returns attributes that must be ignored from the INSERT SQL generation 

.. code-block:: php

    <?php

     $robot = Robots::findFirst();
     print_r($robot->getSkipAttributesOnCreate());




protected  **skipAttributesOnUpdate** (*array* $attributes, [*boolean* $replace])

Sets a list of attributes that must be skipped from the generated UPDATE statement 

.. code-block:: php

    <?php

    class Robots extends \Phalcon\Mvc\Model
    {
    
       public function initialize()
       {
           $this->skipAttributesOnUpdate(array('modified_in'));
       }
    
    }




public *array*  **getSkipAttributesOnUpdate** ()

Returns attributes that must be ignored from the UPDATE SQL generation 

.. code-block:: php

    <?php

     $robot = Robots::findFirst();
     print_r($robot->getSkipAttributesOnUpdate());




public :doc:`Phalcon\\Mvc\\Model\\Relation <Phalcon_Mvc_Model_Relation>`  **hasOne** (*mixed* $fields, *string* $referenceModel, *mixed* $referencedFields, [*array* $options])

Setup a 1-1 relation between two models 

.. code-block:: php

    <?php

    class Robots extends \Phalcon\Mvc\Model
    {
    
       public function initialize()
       {
           $this->hasOne('id', 'RobotsDescription', 'robots_id');
       }
    
    }




public :doc:`Phalcon\\Mvc\\Model\\Relation <Phalcon_Mvc_Model_Relation>`  **belongsTo** (*mixed* $fields, *string* $referenceModel, *mixed* $referencedFields, [*array* $options])

Setup a relation reverse 1-1  between two models 

.. code-block:: php

    <?php

    class RobotsParts extends \Phalcon\Mvc\Model
    {
    
       public function initialize()
       {
           $this->belongsTo('robots_id', 'Robots', 'id');
       }
    
    }




public :doc:`Phalcon\\Mvc\\Model\\Relation <Phalcon_Mvc_Model_Relation>`  **hasMany** (*mixed* $fields, *string* $referenceModel, *mixed* $referencedFields, [*array* $options])

Setup a relation 1-n between two models 

.. code-block:: php

    <?php

    class Robots extends \Phalcon\Mvc\Model
    {
    
       public function initialize()
       {
           $this->hasMany('id', 'RobotsParts', 'robots_id');
       }
    
    }




public :doc:`Phalcon\\Mvc\\Model\\Relation <Phalcon_Mvc_Model_Relation>`  **hasManyToMany** (*string* $fields, *string* $intermediateModel, *string* $intermediateFields, *string* $intermediateReferencedFields, *unknown* $referenceModel, *string* $referencedFields, [*array* $options])

Setup a relation n-n between two models through an intermediate relation 

.. code-block:: php

    <?php

    class Robots extends \Phalcon\Mvc\Model
    {
    
       public function initialize()
       {
           //Setup a many-to-many relation to Parts through RobotsParts
           $this->hasManyToMany(
    		'id',
    		'RobotsParts',
    		'robots_id',
    		'parts_id',
    		'Parts',
    		'id'
    	);
       }
    
    }




public  **addBehavior** (:doc:`Phalcon\\Mvc\\Model\\BehaviorInterface <Phalcon_Mvc_Model_BehaviorInterface>` $behavior)

Setups a behavior in a model 

.. code-block:: php

    <?php

    use Phalcon\Mvc\Model\Behavior\Timestampable;
    
    class Robots extends \Phalcon\Mvc\Model
    {
    
       public function initialize()
       {
    	$this->addBehavior(new Timestampable(array(
    		'onCreate' => array(
    			'field' => 'created_at',
    			'format' => 'Y-m-d'
    		)
    	)));
       }
    
    }




public  **setSnapshotData** (*array* $data, [*array* $columnMap])

Sets the record's snapshot data. This method is used internally to set snapshot data when the model was set up to keep snapshot data



public *boolean*  **hasSnapshotData** ()

Checks if the object has internal snapshot data



public *array*  **getSnapshotData** ()

Returns the internal snapshot data



public *boolean*  **hasChanged** ([*string* $fieldName])

Check if a specific attribute has changed This only works if the model is keeping data snapshots



public *array*  **getChangedFields** ()

Returns a list of changed values



protected  **useDynamicUpdate** (*boolean* $dynamicUpdate)

Sets if a model must use dynamic update instead of the all-field update 

.. code-block:: php

    <?php

    class Robots extends \Phalcon\Mvc\Model
    {
    
       public function initialize()
       {
    	$this->useDynamicUpdate(true);
       }
    
    }




public :doc:`Phalcon\\Mvc\\Model\\ResultsetInterface <Phalcon_Mvc_Model_ResultsetInterface>`  **getRelated** (*string* $alias, [*array* $arguments])

Returns related records based on defined relations



protected *mixed*  **_getRelatedRecords** ()

Returns related records defined relations depending on the method name



public *mixed*  **__call** (*string* $method, [*array* $arguments])

Handles method calls when a method is not implemented



public static *mixed*  **__callStatic** (*string* $method, [*array* $arguments])

Handles method calls when a static method is not implemented



public  **__set** (*string* $property, *mixed* $value)

Magic method to assign values to the the model



public :doc:`Phalcon\\Mvc\\Model\\Resultset <Phalcon_Mvc_Model_Resultset>`  **__get** (*string* $property)

Magic method to get related records using the relation alias as a property



public  **__isset** (*string* $property)

Magic method to check if a property is a valid relation



public *string*  **serialize** ()

Serializes the object ignoring connections, services, related objects or static properties



public  **unserialize** (*string* $data)

Unserializes the object from a serialized string



public *array*  **dump** ()

Returns a simple representation of the object that can be used with var_dump 

.. code-block:: php

    <?php

     var_dump($robot->dump());




public *array*  **toArray** ([*array* $columns], [*bool* $renameColumns], [*unknown* $negate])

Returns the instance as an array representation 

.. code-block:: php

    <?php

     print_r($robot->toArray());




public static  **setup** (*array* $options)

Enables/disables options in the ORM Available options: events                — Enables/Disables globally the internal events virtualForeignKeys    — Enables/Disables virtual foreign keys columnRenaming        — Enables/Disables column renaming notNullValidations    — Enables/Disables automatic not null validation exceptionOnFailedSave — Enables/Disables throws an exception if the saving process fails phqlLiterals          — Enables/Disables literals in PHQL this improves the security of applications propertyMethod        — Enables/Disables property method autoConvert           — Enables/Disables auto convert strict                — Enables/Disables strict mode



public static *boolean*  **remove** (*array* $parameters)

Allows to delete a set of records that match the specified conditions 

.. code-block:: php

    <?php

     $robot = Robots::remove("id=100")




public  **reset** ()

...


protected :doc:`Phalcon\\Mvc\\Model <Phalcon_Mvc_Model>`  **filter** (*string* $field, *string|array* $filters, [*mixed* $defaultValue], [*boolean* $notAllowEmpty], [*boolean* $noRecursive])

Sanitizes a value with a specified single or set of filters 

.. code-block:: php

    <?php

    use Phalcon\Mvc\Model\Validator\ExclusionIn as ExclusionIn;
    
    class Subscriptors extends Phalcon\Mvc\Model
    {
    
    public function filters()
      {
     		$this->filter('status', 'int');
    }
    
    }




public *boolean*  **isRecord** ()

Whether the record is not new and deleted



public *boolean*  **isNewRecord** ()

Whether the record is new and deleted



public *boolean*  **isDeletedRecord** ()

Whether the record is new and deleted



public  **__debugInfo** ()

...


public  **setDbService** (*unknown* $connectionService)

...


public  **getRealAttributes** ()

...


public *array*  **jsonSerialize** ()

Returns serialised model as array for json_encode. 

.. code-block:: php

    <?php

     $robot = Robots::findFirst();
     echo json_encode($robot);




public  **setDI** (:doc:`Phalcon\\DiInterface <Phalcon_DiInterface>` $dependencyInjector) inherited from Phalcon\\Di\\Injectable

Sets the dependency injector



public :doc:`Phalcon\\DiInterface <Phalcon_DiInterface>`  **getDI** ([*unknown* $error], [*unknown* $notUseDefault]) inherited from Phalcon\\Di\\Injectable

Returns the internal dependency injector



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



public  **__sleep** () inherited from Phalcon\\Di\\Injectable

...


