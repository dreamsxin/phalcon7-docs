Abstract class **Phalcon\\Mvc\\Model\\Resultset**
=================================================

*extends* abstract class :doc:`Phalcon\\Di\\Injectable <Phalcon_Di_Injectable>`

*implements* :doc:`Phalcon\\Events\\EventsAwareInterface <Phalcon_Events_EventsAwareInterface>`, :doc:`Phalcon\\Di\\InjectionAwareInterface <Phalcon_Di_InjectionAwareInterface>`, :doc:`Phalcon\\Mvc\\Model\\ResultsetInterface <Phalcon_Mvc_Model_ResultsetInterface>`, Iterator, Traversable, SeekableIterator, Countable, ArrayAccess, Serializable, JsonSerializable

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/mvc/model/resultset.c" class="btn btn-default btn-sm">Source on GitHub</a>`

This component allows to Phalcon\\Mvc\\Model returns large resulsets with the minimum memory consumption Resulsets can be traversed using a standard foreach or a while statement. If a resultset is serialized it will dump all the rows into a big array. Then unserialize will retrieve the rows as they were before serializing.  

.. code-block:: php

    <?php

     //Using a standard foreach
     $robots = Robots::find(array("type='virtual'", "order" => "name"));
     foreach ($robots as $robot) {
      echo $robot->name, "\n";
     }
    
     //Using a while
     $robots = Robots::find(array("type='virtual'", "order" => "name"));
     $robots->rewind();
     while ($robots->valid()) {
      $robot = $robots->current();
      echo $robot->name, "\n";
      $robots->next();
     }



Constants
---------

*integer* **TYPE_RESULT_FULL**

*integer* **TYPE_RESULT_PARTIAL**

*integer* **HYDRATE_RECORDS**

*integer* **HYDRATE_OBJECTS**

*integer* **HYDRATE_ARRAYS**

Methods
-------

public  **next** ()

Moves cursor to next row in the resultset



public *int*  **key** ()

Gets pointer number of active row in the resultset



public  **rewind** ()

Rewinds resultset to its beginning



public  **seek** (*int* $position)

Changes internal pointer to a specific position in the resultset



public *int*  **count** ()

Counts how many rows are in the resultset



public *boolean*  **offsetExists** (*unknown* $property)

Checks whether offset exists in the resultset



public :doc:`Phalcon\\Mvc\\ModelInterface <Phalcon_Mvc_ModelInterface>`  **offsetGet** (*unknown* $property)

Gets row in a specific position of the resultset



public  **offsetSet** (*unknown* $property, :doc:`Phalcon\\Mvc\\ModelInterface <Phalcon_Mvc_ModelInterface>` $value)

Resultsets cannot be changed. It has only been implemented to meet the definition of the ArrayAccess interface



public  **offsetUnset** (*unknown* $property)

Resultsets cannot be changed. It has only been implemented to meet the definition of the ArrayAccess interface



public *int*  **getType** ()

Returns the internal type of data retrieval that the resultset is using



public :doc:`Phalcon\\Mvc\\ModelInterface <Phalcon_Mvc_ModelInterface>`  **getFirst** ()

Get first row in the resultset



public :doc:`Phalcon\\Mvc\\ModelInterface <Phalcon_Mvc_ModelInterface>`  **getLast** ()

Get last row in the resultset



public :doc:`Phalcon\\Mvc\\Model\\Resultset <Phalcon_Mvc_Model_Resultset>`  **setIsFresh** (*boolean* $isFresh)

Set if the resultset is fresh or an old one cached



public *boolean*  **isFresh** ()

Tell if the resultset if fresh or an old one cached



public :doc:`Phalcon\\Mvc\\Model\\Resultset <Phalcon_Mvc_Model_Resultset>`  **setHydrateMode** (*int* $hydrateMode)

Sets the hydration mode in the resultset



public *int*  **getHydrateMode** ()

Returns the current hydration mode



public :doc:`Phalcon\\Cache\\BackendInterface <Phalcon_Cache_BackendInterface>`  **getCache** ()

Returns the associated cache for the resultset



public :doc:`Phalcon\\Mvc\\ModelInterface <Phalcon_Mvc_ModelInterface>`  **current** ()

Returns current row in the resultset



public *Phalcon\\Mvc\\Model\\MessageInterface[]*  **getMessages** ()

Returns the error messages produced by a batch operation



public *boolean*  **delete** ([*Closure* $conditionCallback])

Deletes every record in the resultset



public :doc:`Phalcon\\Mvc\\Model <Phalcon_Mvc_Model>` [] **filter** (*callback* $filter)

Filters a resultset returning only those the developer requires 

.. code-block:: php

    <?php

     $filtered = $robots->filter(function($robot){
    	if ($robot->id < 3) {
    		return $robot;
    	}
    });




public *boolean*  **update** (*array* $data, [*Closure* $conditionCallback])

Updates every record in the resultset



public *array*  **jsonSerialize** ()

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


abstract public *array*  **toArray** () inherited from Phalcon\\Mvc\\Model\\ResultsetInterface

Returns a complete resultset as an array, if the resultset has a big number of rows it could consume more memory than currently it does.



abstract public  **valid** () inherited from Iterator

...


abstract public  **serialize** () inherited from Serializable

...


abstract public  **unserialize** (*unknown* $serialized) inherited from Serializable

...


