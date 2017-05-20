Class **Phalcon\\Mvc\\Model\\Query**
====================================

*extends* abstract class :doc:`Phalcon\\Di\\Injectable <Phalcon_Di_Injectable>`

*implements* :doc:`Phalcon\\Events\\EventsAwareInterface <Phalcon_Events_EventsAwareInterface>`, :doc:`Phalcon\\Di\\InjectionAwareInterface <Phalcon_Di_InjectionAwareInterface>`, :doc:`Phalcon\\Mvc\\Model\\QueryInterface <Phalcon_Mvc_Model_QueryInterface>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/mvc/model/query.c" class="btn btn-default btn-sm">Source on GitHub</a>`

This class takes a PHQL intermediate representation and executes it.  

.. code-block:: php

    <?php

     $phql = "SELECT c.price*0.16 AS taxes, c.* FROM Cars AS c JOIN Brands AS b
              WHERE b.name = :name: ORDER BY c.name";
    
     $result = $manager->executeQuery($phql, array(
       'name' => 'Lamborghini'
     ));
    
     foreach ($result as $row) {
       echo "Name: ", $row->cars->name, "\n";
       echo "Price: ", $row->cars->price, "\n";
       echo "Taxes: ", $row->taxes, "\n";
     }



Constants
---------

*integer* **TYPE_SELECT**

*integer* **TYPE_INSERT**

*integer* **TYPE_UPDATE**

*integer* **TYPE_DELETE**

Methods
-------

public  **__construct** (*string* $phql)

Phalcon\\Mvc\\Model\\Query constructor



public  **setPhql** ([*unknown* $phql])

...


public  **getPhql** ()

...


public :doc:`Phalcon\\Mvc\\Model\\ManagerInterface <Phalcon_Mvc_Model_ManagerInterface>`  **getModelsManager** ()

Returns the models manager related to the entity instance



public :doc:`Phalcon\\Mvc\\Model\\MetaDataInterface <Phalcon_Mvc_Model_MetaDataInterface>`  **getModelsMetaData** ()

Returns the models meta-data service related to the entity instance



public :doc:`Phalcon\\Mvc\\Model\\Query <Phalcon_Mvc_Model_Query>`  **setUniqueRow** (*boolean* $uniqueRow)

Tells to the query if only the first row in the resultset must be returned



public *boolean*  **getUniqueRow** ()

Check if the query is programmed to get only the first row in the resultset



protected *string*  **_getQualified** ()

Replaces the model's name to its source name in a qualifed-name expression



protected *string*  **_getCallArgument** ()

Resolves a expression in a single call argument



protected *string*  **_getCaseExpression** ()

Resolves a expression in a single call argument



protected *string*  **_getFunctionCall** ()

Resolves a expression in a single call argument



protected *string*  **_getExpression** ()

Resolves an expression from its intermediate code into a string



protected *array*  **_getSelectColumn** ()

Resolves a column from its intermediate representation into an array used to determine if the resulset produced is simple or complex



protected *string*  **_getTable** ()

Resolves a table in a SELECT statement checking if the model exists



protected *array*  **_getJoin** ()

Resolves a JOIN clause checking if the associated models exist



protected *string*  **_getJoinType** ()

Resolves a JOIN type



protected *array*  **_getSingleJoin** ()

Resolves joins involving has-one/belongs-to/has-many relations



protected *array*  **_getMultiJoin** ()

Resolves joins involving many-to-many relations



protected *array*  **_getJoins** ()

Processes the JOINs in the query returning an internal representation for the database dialect



protected *string*  **_getOrderClause** ()

Returns a processed order clause for a SELECT statement



protected *string*  **_getGroupClause** ()

Returns a processed group clause for a SELECT statement



protected  **_getLimitClause** ()

...


protected *array*  **_prepareSelect** ()

Analyzes a SELECT intermediate code and produces an array to be executed later



protected *array*  **_prepareInsert** ()

Analyzes an INSERT intermediate code and produces an array to be executed later



protected *array*  **_prepareUpdate** ()

Analyzes an UPDATE intermediate code and produces an array to be executed later



protected *array*  **_prepareDelete** ()

Analyzes a DELETE intermediate code and produces an array to be executed later



public *array*  **parse** ()

Parses the intermediate code produced by Phalcon\\Mvc\\Model\\Query\\Lang generating another intermediate representation that could be executed by Phalcon\\Mvc\\Model\\Query



public :doc:`Phalcon\\Mvc\\Model\\Query <Phalcon_Mvc_Model_Query>`  **cache** (*array* $cacheOptions)

Sets the cache parameters of the query



public  **getCacheOptions** ()

Returns the current cache options



public :doc:`Phalcon\\Cache\\BackendInterface <Phalcon_Cache_BackendInterface>`  **getCache** ()

Returns the current cache backend instance



protected :doc:`Phalcon\\Mvc\\Model\\ResultsetInterface <Phalcon_Mvc_Model_ResultsetInterface>`  **_executeSelect** ()

Executes the SELECT intermediate representation producing a Phalcon\\Mvc\\Model\\Resultset



protected :doc:`Phalcon\\Mvc\\Model\\Query\\StatusInterface <Phalcon_Mvc_Model_Query_StatusInterface>`  **_executeInsert** ()

Executes the INSERT intermediate representation producing a Phalcon\\Mvc\\Model\\Query\\Status



protected :doc:`Phalcon\\Mvc\\Model\\Query\\StatusInterface <Phalcon_Mvc_Model_Query_StatusInterface>`  **_executeUpdate** ()

Executes the UPDATE intermediate representation producing a Phalcon\\Mvc\\Model\\Query\\Status



protected :doc:`Phalcon\\Mvc\\Model\\Query\\StatusInterface <Phalcon_Mvc_Model_Query_StatusInterface>`  **_executeDelete** ()

Executes the DELETE intermediate representation producing a Phalcon\\Mvc\\Model\\Query\\Status



public *mixed*  **execute** ([*array* $bindParams], [*array* $bindTypes], [*unknown* $useRawsql])

Executes a parsed PHQL statement



public :doc:`Phalcon\\Mvc\\ModelInterface <Phalcon_Mvc_ModelInterface>`  **getSingleResult** ([*array* $bindParams], [*array* $bindTypes])

Executes the query returning the first result



public :doc:`Phalcon\\Mvc\\Model\\Query <Phalcon_Mvc_Model_Query>`  **setType** (*int* $type)

Sets the type of PHQL statement to be executed



public *int*  **getType** ()

Gets the type of PHQL statement executed



public *mixed*  **getBindParam** (*string* $name)

Get bind parameter



public :doc:`Phalcon\\Mvc\\Model\\Query <Phalcon_Mvc_Model_Query>`  **setBindParams** (*array* $bindParams)

Set default bind parameters



public *array*  **getBindParams** ()

Returns default bind params



public :doc:`Phalcon\\Mvc\\Model\\Query <Phalcon_Mvc_Model_Query>`  **setMergeBindParams** (*array* $bindParams)

Set merge bind parameters



public *array*  **getMergeBindParams** ()

Returns merge bind params



public :doc:`Phalcon\\Mvc\\Model\\Query <Phalcon_Mvc_Model_Query>`  **setBindType** (*string* $name, *int* $type)

Set bind type



public :doc:`Phalcon\\Mvc\\Model\\Query <Phalcon_Mvc_Model_Query>`  **setBindTypes** (*array* $bindTypes)

Set default bind types



public *array*  **getBindTypes** ()

Returns default bind types



public :doc:`Phalcon\\Mvc\\Model\\Query <Phalcon_Mvc_Model_Query>`  **setMergeBindTypes** (*array* $bindTypes)

Set merge bind types



public *array*  **getMergeBindTypes** ()

Returns default bind types



public :doc:`Phalcon\\Mvc\\Model\\Query <Phalcon_Mvc_Model_Query>`  **setIntermediate** (*array* $intermediate)

Allows to set the IR to be executed



public *array*  **getIntermediate** ()

Returns the intermediate representation of the PHQL statement



public *array*  **getModels** ()

Returns the models of the PHQL statement



public :doc:`Phalcon\\Mvc\\Model\\Query <Phalcon_Mvc_Model_Query>`  **setConnection** (:doc:`Phalcon\\Db\\AdapterInterface <Phalcon_Db_AdapterInterface>` $connection)

Sets the connection



public *mixed*  **getConnection** ()

Gets the connection



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


