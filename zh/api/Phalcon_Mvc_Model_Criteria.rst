Class **Phalcon\\Mvc\\Model\\Criteria**
=======================================

*extends* abstract class :doc:`Phalcon\\Di\\Injectable <Phalcon_Di_Injectable>`

*implements* :doc:`Phalcon\\Events\\EventsAwareInterface <Phalcon_Events_EventsAwareInterface>`, :doc:`Phalcon\\Di\\InjectionAwareInterface <Phalcon_Di_InjectionAwareInterface>`, :doc:`Phalcon\\Mvc\\Model\\CriteriaInterface <Phalcon_Mvc_Model_CriteriaInterface>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/mvc/model/criteria.c" class="btn btn-default btn-sm">Source on GitHub</a>`

This class allows to build the array parameter required by Phalcon\\Mvc\\Model::find and Phalcon\\Mvc\\Model::findFirst using an object-oriented interface  

.. code-block:: php

    <?php

    $robots = Robots::query()
        ->where("type = :type:")
        ->andWhere("year < 2000")
        ->bind(array("type" => "mechanical"))
        ->order("name")
        ->execute();



Methods
-------

public :doc:`Phalcon\\Mvc\\Model\\CriteriaInterface <Phalcon_Mvc_Model_CriteriaInterface>`  **setModelName** (*string* $modelName)

Set a model on which the query will be executed



public *string*  **getModelName** ()

Returns an internal model name on which the criteria will be applied



public :doc:`Phalcon\\Mvc\\Model\\CriteriaInterface <Phalcon_Mvc_Model_CriteriaInterface>`  **bind** (*string* $bindParams, [*boolean* $merge])

Sets the bound parameters in the criteria This method replaces all previously set bound parameters



public :doc:`Phalcon\\Mvc\\Model\\CriteriaInterface <Phalcon_Mvc_Model_CriteriaInterface>`  **bindTypes** (*array* $bindTypes, [*unknown* $merge])

Sets the bind types in the criteria This method replaces all previously set bound parameters



public  **select** (*unknown* $columns)

...


public :doc:`Phalcon\\Mvc\\Model\\CriteriaInterface <Phalcon_Mvc_Model_CriteriaInterface>`  **columns** (*string|array* $columns)

Sets the columns to be queried 

.. code-block:: php

    <?php

    $criteria->columns(array('id', 'name'));




public *string|array*  **getColumns** ()

Returns the columns to be queried



public :doc:`Phalcon\\Mvc\\Model\\CriteriaInterface <Phalcon_Mvc_Model_CriteriaInterface>`  **join** (*string* $model, [*string* $conditions], [*string* $alias], [*string* $type])

Adds a join to the query 

.. code-block:: php

    <?php

    $criteria->join('Robots');
    $criteria->join('Robots', 'r.id = RobotsParts.robots_id');
    $criteria->join('Robots', 'r.id = RobotsParts.robots_id', 'r');
    $criteria->join('Robots', 'r.id = RobotsParts.robots_id', 'r', 'LEFT');




public :doc:`Phalcon\\Mvc\\Model\\CriteriaInterface <Phalcon_Mvc_Model_CriteriaInterface>`  **innerJoin** (*string* $model, [*string* $conditions], [*string* $alias])

Adds a INNER join to the query 

.. code-block:: php

    <?php

    $criteria->innerJoin('Robots');
    $criteria->innerJoin('Robots', 'r.id = RobotsParts.robots_id');
    $criteria->innerJoin('Robots', 'r.id = RobotsParts.robots_id', 'r');
    $criteria->innerJoin('Robots', 'r.id = RobotsParts.robots_id', 'r', 'LEFT');




public :doc:`Phalcon\\Mvc\\Model\\CriteriaInterface <Phalcon_Mvc_Model_CriteriaInterface>`  **leftJoin** (*string* $model, [*string* $conditions], [*string* $alias])

Adds a LEFT join to the query 

.. code-block:: php

    <?php

    $criteria->leftJoin('Robots', 'r.id = RobotsParts.robots_id', 'r');




public :doc:`Phalcon\\Mvc\\Model\\CriteriaInterface <Phalcon_Mvc_Model_CriteriaInterface>`  **rightJoin** (*string* $model, [*string* $conditions], [*string* $alias])

Adds a RIGHT join to the query 

.. code-block:: php

    <?php

    $criteria->rightJoin('Robots', 'r.id = RobotsParts.robots_id', 'r');




public :doc:`Phalcon\\Mvc\\Model\\CriteriaInterface <Phalcon_Mvc_Model_CriteriaInterface>`  **where** (*string* $conditions, [*array* $bindParams], [*array* $bindTypes])

Sets the conditions parameter in the criteria



public :doc:`Phalcon\\Mvc\\Model\\CriteriaInterface <Phalcon_Mvc_Model_CriteriaInterface>`  **addWhere** (*string* $conditions, [*array* $bindParams], [*array* $bindTypes])

Appends a condition to the current conditions using an AND operator (deprecated)



public :doc:`Phalcon\\Mvc\\Model\\CriteriaInterface <Phalcon_Mvc_Model_CriteriaInterface>`  **andWhere** (*string* $conditions, [*array* $bindParams], [*array* $bindTypes])

Appends a condition to the current conditions using an AND operator



public :doc:`Phalcon\\Mvc\\Model\\CriteriaInterface <Phalcon_Mvc_Model_CriteriaInterface>`  **orWhere** (*string* $conditions, [*array* $bindParams], [*array* $bindTypes])

Appends a condition to the current conditions using an OR operator



public :doc:`Phalcon\\Mvc\\Model\\CriteriaInterface <Phalcon_Mvc_Model_CriteriaInterface>`  **betweenWhere** (*string* $expr, *mixed* $minimum, *mixed* $maximum, [*boolean* $useOrWhere])

Appends a BETWEEN condition to the current conditions 

.. code-block:: php

    <?php

    $criteria->betweenWhere('price', 100.25, 200.50);




public :doc:`Phalcon\\Mvc\\Model\\CriteriaInterface <Phalcon_Mvc_Model_CriteriaInterface>`  **notBetweenWhere** (*string* $expr, *mixed* $minimum, *mixed* $maximum, [*boolean* $useOrWhere])

Appends a NOT BETWEEN condition to the current conditions 

.. code-block:: php

    <?php

    $criteria->notBetweenWhere('price', 100.25, 200.50);




public :doc:`Phalcon\\Mvc\\Model\\CriteriaInterface <Phalcon_Mvc_Model_CriteriaInterface>`  **inWhere** (*string* $expr, *array* $values, [*unknown* $useOrWhere])

Appends an IN condition to the current conditions 

.. code-block:: php

    <?php

    $criteria->inWhere('id', [1, 2, 3]);




public :doc:`Phalcon\\Mvc\\Model\\CriteriaInterface <Phalcon_Mvc_Model_CriteriaInterface>`  **notInWhere** (*string* $expr, *array* $values, [*boolean* $useOrWhere])

Appends a NOT IN condition to the current conditions 

.. code-block:: php

    <?php

    $criteria->notInWhere('id', [1, 2, 3]);




public *string*  **getWhere** ()

Returns the conditions parameter in the criteria



public :doc:`Phalcon\\Mvc\\Model\\CriteriaInterface <Phalcon_Mvc_Model_CriteriaInterface>`  **conditions** (*string* $conditions)

Adds the conditions parameter to the criteria



public *string*  **getConditions** ()

Returns the conditions parameter in the criteria



public :doc:`Phalcon\\Mvc\\Model\\CriteriaInterface <Phalcon_Mvc_Model_CriteriaInterface>`  **order** (*string* $orderColumns)

Adds the order-by parameter to the criteria (deprecated)



public :doc:`Phalcon\\Mvc\\Model\\CriteriaInterface <Phalcon_Mvc_Model_CriteriaInterface>`  **orderBy** (*string* $orderColumns)

Adds the order-by parameter to the criteria



public *string*  **getOrder** ()

Returns the order parameter in the criteria



public :doc:`Phalcon\\Mvc\\Model\\CriteriaInterface <Phalcon_Mvc_Model_CriteriaInterface>`  **limit** (*int* $limit, [*int* $offset])

Adds the limit parameter to the criteria



public *int*  **getLimit** ()

Returns the limit parameter in the criteria



public :doc:`Phalcon\\Mvc\\Model\\CriteriaInterface <Phalcon_Mvc_Model_CriteriaInterface>`  **setUniqueRow** (*boolean* $uniqueRow)

Tells to the query if only the first row in the resultset must be returned



public *boolean*  **getUniqueRow** ()

Check if the query is programmed to get only the first row in the resultset



public :doc:`Phalcon\\Mvc\\Model\\CriteriaInterface <Phalcon_Mvc_Model_CriteriaInterface>`  **forUpdate** ([*boolean* $forUpdate])

Adds the "for_update" parameter to the criteria



public :doc:`Phalcon\\Mvc\\Model\\CriteriaInterface <Phalcon_Mvc_Model_CriteriaInterface>`  **sharedLock** ([*boolean* $sharedLock])

Adds the "shared_lock" parameter to the criteria



public *array*  **getParams** ()

Returns all the parameters defined in the criteria



public static :doc:`Phalcon\\Mvc\\Model\\Criteria <Phalcon_Mvc_Model_Criteria>`  **fromInput** (:doc:`Phalcon\\DiInterface <Phalcon_DiInterface>` $dependencyInjector, *string* $modelName, *array* $data)

Builds a Phalcon\\Mvc\\Model\\Criteria based on an input array like $_POST



public static :doc:`Phalcon\\Mvc\\Model\\Criteria <Phalcon_Mvc_Model_Criteria>`  **groupBy** (*string* $group)

Sets a GROUP BY clause



public :doc:`Phalcon\\Mvc\\Model\\Criteria <Phalcon_Mvc_Model_Criteria>`  **having** (*string* $having)

Sets a HAVING condition clause. You need to escape PHQL reserved words using [ and ] delimiters



public :doc:`Phalcon\\Mvc\\Model\\ResultsetInterface <Phalcon_Mvc_Model_ResultsetInterface>`  **execute** ()

Executes a find using the parameters built with the criteria



public *int*  **count** ([*unknown* $column])

Auto sets columns and return execute



public :doc:`Phalcon\\Mvc\\Model\\CriteriaInterface <Phalcon_Mvc_Model_CriteriaInterface>`  **cache** (*array* $options)

Sets the cache options in the criteria This method replaces all previously set cache options



public :doc:`Phalcon\\Mvc\\Model\\CriteriaInterface <Phalcon_Mvc_Model_CriteriaInterface>`  **insert** ()

Sets insert type of PHQL statement to be executed



public :doc:`Phalcon\\Mvc\\Model\\CriteriaInterface <Phalcon_Mvc_Model_CriteriaInterface>`  **update** ()

Sets update type of PHQL statement to be executed



public :doc:`Phalcon\\Mvc\\Model\\CriteriaInterface <Phalcon_Mvc_Model_CriteriaInterface>`  **delete** ()

Sets update type of PHQL statement to be executed



public *string*  **getPhql** ()

Returns a PHQL statement built with the criteria



public *string*  **_generateSelect** ()

Returns a PHQL statement built with the criteria



public *string*  **_generateInsert** ()

Returns a PHQL statement built with the criteria



public *string*  **_generateUpdate** ()

Returns a PHQL statement built with the criteria



public *string*  **_generateDelete** ()

Returns a PHQL statement built with the criteria



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


