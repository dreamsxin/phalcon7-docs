Class **Phalcon\\Mvc\\Model\\Resultset\\Complex**
=================================================

*extends* abstract class :doc:`Phalcon\\Mvc\\Model\\Resultset <Phalcon_Mvc_Model_Resultset>`

*implements* JsonSerializable, Serializable, ArrayAccess, Countable, SeekableIterator, Traversable, Iterator, :doc:`Phalcon\\Mvc\\Model\\ResultsetInterface <Phalcon_Mvc_Model_ResultsetInterface>`, :doc:`Phalcon\\Di\\InjectionAwareInterface <Phalcon_Di_InjectionAwareInterface>`, :doc:`Phalcon\\Events\\EventsAwareInterface <Phalcon_Events_EventsAwareInterface>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/mvc/model/resultset/complex.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Complex resultsets may include complete objects and scalar values. This class builds every complex row as it is required


Constants
---------

*integer* **TYPE_RESULT_FULL**

*integer* **TYPE_RESULT_PARTIAL**

*integer* **HYDRATE_RECORDS**

*integer* **HYDRATE_OBJECTS**

*integer* **HYDRATE_ARRAYS**

Methods
-------

public  **__construct** (*array* $columnsTypes, :doc:`Phalcon\\Db\\ResultInterface <Phalcon_Db_ResultInterface>` $result, [:doc:`Phalcon\\Cache\\BackendInterface <Phalcon_Cache_BackendInterface>` $cache], [:doc:`Phalcon\\Mvc\\ModelInterface <Phalcon_Mvc_ModelInterface>` $sourceModel])

Phalcon\\Mvc\\Model\\Resultset\\Complex constructor



public *boolean*  **valid** ()

Check whether internal resource has rows to fetch



public *array*  **toArray** ()

Returns a complete resultset as an array, if the resultset has a big number of rows it could consume more memory than currently it does.



public *string*  **serialize** ()

Serializing a resultset will dump all related rows into a big array



public  **unserialize** ([*unknown* $serialized])

Unserializing a resultset will allow to only works on the rows present in the saved state



public  **next** () inherited from Phalcon\\Mvc\\Model\\Resultset

Moves cursor to next row in the resultset



public *int*  **key** () inherited from Phalcon\\Mvc\\Model\\Resultset

Gets pointer number of active row in the resultset



public  **rewind** () inherited from Phalcon\\Mvc\\Model\\Resultset

Rewinds resultset to its beginning



public  **seek** (*int* $position) inherited from Phalcon\\Mvc\\Model\\Resultset

Changes internal pointer to a specific position in the resultset



public *int*  **count** () inherited from Phalcon\\Mvc\\Model\\Resultset

Counts how many rows are in the resultset



public *boolean*  **offsetExists** (*unknown* $property) inherited from Phalcon\\Mvc\\Model\\Resultset

Checks whether offset exists in the resultset



public :doc:`Phalcon\\Mvc\\ModelInterface <Phalcon_Mvc_ModelInterface>`  **offsetGet** (*unknown* $property) inherited from Phalcon\\Mvc\\Model\\Resultset

Gets row in a specific position of the resultset



public  **offsetSet** (*unknown* $property, :doc:`Phalcon\\Mvc\\ModelInterface <Phalcon_Mvc_ModelInterface>` $value) inherited from Phalcon\\Mvc\\Model\\Resultset

Resultsets cannot be changed. It has only been implemented to meet the definition of the ArrayAccess interface



public  **offsetUnset** (*unknown* $property) inherited from Phalcon\\Mvc\\Model\\Resultset

Resultsets cannot be changed. It has only been implemented to meet the definition of the ArrayAccess interface



public *int*  **getType** () inherited from Phalcon\\Mvc\\Model\\Resultset

Returns the internal type of data retrieval that the resultset is using



public :doc:`Phalcon\\Mvc\\ModelInterface <Phalcon_Mvc_ModelInterface>`  **getFirst** () inherited from Phalcon\\Mvc\\Model\\Resultset

Get first row in the resultset



public :doc:`Phalcon\\Mvc\\ModelInterface <Phalcon_Mvc_ModelInterface>`  **getLast** () inherited from Phalcon\\Mvc\\Model\\Resultset

Get last row in the resultset



public :doc:`Phalcon\\Mvc\\Model\\Resultset <Phalcon_Mvc_Model_Resultset>`  **setIsFresh** (*boolean* $isFresh) inherited from Phalcon\\Mvc\\Model\\Resultset

Set if the resultset is fresh or an old one cached



public *boolean*  **isFresh** () inherited from Phalcon\\Mvc\\Model\\Resultset

Tell if the resultset if fresh or an old one cached



public :doc:`Phalcon\\Mvc\\Model\\Resultset <Phalcon_Mvc_Model_Resultset>`  **setHydrateMode** (*int* $hydrateMode) inherited from Phalcon\\Mvc\\Model\\Resultset

Sets the hydration mode in the resultset



public *int*  **getHydrateMode** () inherited from Phalcon\\Mvc\\Model\\Resultset

Returns the current hydration mode



public :doc:`Phalcon\\Cache\\BackendInterface <Phalcon_Cache_BackendInterface>`  **getCache** () inherited from Phalcon\\Mvc\\Model\\Resultset

Returns the associated cache for the resultset



public :doc:`Phalcon\\Mvc\\ModelInterface <Phalcon_Mvc_ModelInterface>`  **current** () inherited from Phalcon\\Mvc\\Model\\Resultset

Returns current row in the resultset



public *Phalcon\\Mvc\\Model\\MessageInterface[]*  **getMessages** () inherited from Phalcon\\Mvc\\Model\\Resultset

Returns the error messages produced by a batch operation



public *boolean*  **delete** ([*Closure* $conditionCallback]) inherited from Phalcon\\Mvc\\Model\\Resultset

Deletes every record in the resultset



public :doc:`Phalcon\\Mvc\\Model <Phalcon_Mvc_Model>` [] **filter** (*callback* $filter) inherited from Phalcon\\Mvc\\Model\\Resultset

Filters a resultset returning only those the developer requires 

.. code-block:: php

    <?php

     $filtered = $robots->filter(function($robot){
    	if ($robot->id < 3) {
    		return $robot;
    	}
    });




public *boolean*  **update** (*array* $data, [*Closure* $conditionCallback]) inherited from Phalcon\\Mvc\\Model\\Resultset

Updates every record in the resultset



public *array*  **jsonSerialize** () inherited from Phalcon\\Mvc\\Model\\Resultset

Returns serialised model objects as array for json_encode. Calls jsonSerialize on each object if present 

.. code-block:: php

    <?php

     $robots = Robots::find();
     echo json_encode($robots);




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


