Interface **Phalcon\\Mvc\\Model\\CriteriaInterface**
====================================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/phalcon/mvc/model/criteriainterface.zep" class="btn btn-default btn-sm">Source on GitHub</a>`

Phalcon\\Mvc\\Model\\CriteriaInterface initializer


Methods
-------

abstract public :doc:`Phalcon\\Mvc\\Model\\CriteriaInterface <Phalcon_Mvc_Model_CriteriaInterface>`  **setModelName** (*string* $modelName)

Set a model on which the query will be executed



abstract public *string*  **getModelName** ()

Returns an internal model name on which the criteria will be applied



abstract public :doc:`Phalcon\\Mvc\\Model\\CriteriaInterface <Phalcon_Mvc_Model_CriteriaInterface>`  **bind** (*array* $bindParams, [*unknown* $merge])

Adds the bind parameter to the criteria



abstract public :doc:`Phalcon\\Mvc\\Model\\CriteriaInterface <Phalcon_Mvc_Model_CriteriaInterface>`  **bindTypes** (*array* $bindTypes, [*unknown* $merge])

Sets the bind types in the criteria This method replaces all previously set bound parameters



abstract public :doc:`Phalcon\\Mvc\\Model\\CriteriaInterface <Phalcon_Mvc_Model_CriteriaInterface>`  **columns** (*string|array* $columns)

Sets the columns to be queried 

.. code-block:: php

    <?php

    $criteria->columns(array('id', 'name'));




abstract public :doc:`Phalcon\\Mvc\\Model\\CriteriaInterface <Phalcon_Mvc_Model_CriteriaInterface>`  **join** (*string* $model, [*string* $conditions], [*string* $alias], [*string* $type])

Adds a join to the query 

.. code-block:: php

    <?php

    $criteria->join('Robots');
    $criteria->join('Robots', 'r.id = RobotsParts.robots_id');
    $criteria->join('Robots', 'r.id = RobotsParts.robots_id', 'r');
    $criteria->join('Robots', 'r.id = RobotsParts.robots_id', 'r', 'LEFT');




abstract public :doc:`Phalcon\\Mvc\\Model\\CriteriaInterface <Phalcon_Mvc_Model_CriteriaInterface>`  **where** (*string* $conditions, [*array* $bindParams], [*array* $bindTypes])

Adds the conditions parameter to the criteria



abstract public :doc:`Phalcon\\Mvc\\Model\\CriteriaInterface <Phalcon_Mvc_Model_CriteriaInterface>`  **andWhere** (*string* $conditions, [*array* $bindParams], [*array* $bindTypes])

Appends a condition to the current conditions using an AND operator



abstract public :doc:`Phalcon\\Mvc\\Model\\CriteriaInterface <Phalcon_Mvc_Model_CriteriaInterface>`  **orWhere** (*string* $conditions, [*array* $bindParams], [*array* $bindTypes])

Appends a condition to the current conditions using an OR operator



abstract public :doc:`Phalcon\\Mvc\\Model\\CriteriaInterface <Phalcon_Mvc_Model_CriteriaInterface>`  **betweenWhere** (*string* $expr, *mixed* $minimum, *mixed* $maximum, [*unknown* $useOrWhere])

Appends a BETWEEN condition to the current conditions 

.. code-block:: php

    <?php

    $criteria->betweenWhere('price', 100.25, 200.50);




abstract public :doc:`Phalcon\\Mvc\\Model\\CriteriaInterface <Phalcon_Mvc_Model_CriteriaInterface>`  **notBetweenWhere** (*string* $expr, *mixed* $minimum, *mixed* $maximum, [*unknown* $useOrWhere])

Appends a NOT BETWEEN condition to the current conditions 

.. code-block:: php

    <?php

    $criteria->notBetweenWhere('price', 100.25, 200.50);




abstract public :doc:`Phalcon\\Mvc\\Model\\CriteriaInterface <Phalcon_Mvc_Model_CriteriaInterface>`  **inWhere** (*string* $expr, *array* $values, [*unknown* $useOrWhere])

Appends an IN condition to the current conditions 

.. code-block:: php

    <?php

    $criteria->inWhere('id', [1, 2, 3]);




abstract public :doc:`Phalcon\\Mvc\\Model\\CriteriaInterface <Phalcon_Mvc_Model_CriteriaInterface>`  **notInWhere** (*string* $expr, *array* $values, [*unknown* $useOrWhere])

Appends a NOT IN condition to the current conditions 

.. code-block:: php

    <?php

    $criteria->notInWhere('id', [1, 2, 3]);




abstract public *string*  **getWhere** ()

Returns the conditions parameter in the criteria



abstract public :doc:`Phalcon\\Mvc\\Model\\CriteriaInterface <Phalcon_Mvc_Model_CriteriaInterface>`  **conditions** (*string* $conditions)

Adds the conditions parameter to the criteria



abstract public *string|array*  **getColumns** ()

Returns the columns to be queried



abstract public *string*  **getConditions** ()

Returns the conditions parameter in the criteria



abstract public :doc:`Phalcon\\Mvc\\Model\\CriteriaInterface <Phalcon_Mvc_Model_CriteriaInterface>`  **orderBy** (*string* $orderColumns)

Adds the order-by parameter to the criteria



abstract public *string*  **getOrder** ()

Returns the order parameter in the criteria



abstract public :doc:`Phalcon\\Mvc\\Model\\CriteriaInterface <Phalcon_Mvc_Model_CriteriaInterface>`  **limit** (*int* $limit, [*int* $offset])

Sets the limit parameter to the criteria



abstract public *int*  **getLimit** ()

Returns the limit parameter in the criteria



abstract public  **setUniqueRow** (*unknown* $uniqueRow)

...


abstract public  **getUniqueRow** ()

...


abstract public :doc:`Phalcon\\Mvc\\Model\\CriteriaInterface <Phalcon_Mvc_Model_CriteriaInterface>`  **forUpdate** ([*boolean* $forUpdate])

Sets the "for_update" parameter to the criteria



abstract public :doc:`Phalcon\\Mvc\\Model\\CriteriaInterface <Phalcon_Mvc_Model_CriteriaInterface>`  **sharedLock** ([*boolean* $sharedLock])

Sets the "shared_lock" parameter to the criteria



abstract public *array*  **getParams** ()

Returns all the parameters defined in the criteria



abstract public static :doc:`Phalcon\\Mvc\\Model\\CriteriaInterface <Phalcon_Mvc_Model_CriteriaInterface>`  **fromInput** (:doc:`Phalcon\\DiInterface <Phalcon_DiInterface>` $dependencyInjector, *string* $modelName, *array* $data)

Builds a Phalcon\\Mvc\\Model\\Criteria based on an input array like $_POST



abstract public :doc:`Phalcon\\Mvc\\Model\\ResultsetInterface <Phalcon_Mvc_Model_ResultsetInterface>`  **execute** ()

Executes a find using the parameters built with the criteria



abstract public :doc:`Phalcon\\Mvc\\Model\\CriteriaInterface <Phalcon_Mvc_Model_CriteriaInterface>`  **insert** ()

Set columns for an insert 

.. code-block:: php

    <?php

    $criteria->insert(array('name', 'type'), array(array('phalcon', 1), array('zephir', 2)));




abstract public :doc:`Phalcon\\Mvc\\Model\\CriteriaInterface <Phalcon_Mvc_Model_CriteriaInterface>`  **update** ()

Set columns for an update 

.. code-block:: php

    <?php

    $criteria->update(array('name' => 'phalcon'));




abstract public :doc:`Phalcon\\Mvc\\Model\\CriteriaInterface <Phalcon_Mvc_Model_CriteriaInterface>`  **delete** ()

Set the table for a delete.



abstract public *String*  **getPhql** ()

Returns a PHQL statement built with the criteria



