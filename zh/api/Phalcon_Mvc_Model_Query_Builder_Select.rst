Class **Phalcon\\Mvc\\Model\\Query\\Builder\\Select**
=====================================================

*extends* abstract class :doc:`Phalcon\\Mvc\\Model\\Query\\Builder\\Join <Phalcon_Mvc_Model_Query_Builder_Join>`

*implements* :doc:`Phalcon\\Mvc\\Model\\Query\\BuilderInterface <Phalcon_Mvc_Model_Query_BuilderInterface>`, :doc:`Phalcon\\DI\\InjectionAwareInterface <Phalcon_DI_InjectionAwareInterface>`, :doc:`Phalcon\\Events\\EventsAwareInterface <Phalcon_Events_EventsAwareInterface>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/mvc/model/query/builder/select.c" class="btn btn-default btn-sm">Source on GitHub</a>`


.. code-block:: php

    <?php

    $resultset = $this->modelsManager->createBuilder()
       ->from('Robots')
       ->join('RobotsParts')
       ->limit(20)
       ->orderBy('Robots.name')
       ->getQuery()
       ->execute();



Methods
-------

public  **__construct** ([*array* $params])

Phalcon\\Mvc\\Model\\Query\\Builder\\Select constructor 

.. code-block:: php

    <?php

     $params = array(
        'models'     => array('Users'),
        'columns'    => array('id', 'name', 'status'),
        'conditions' => array(
            array(
                "created > :min: AND created < :max:",
                array("min" => '2013-01-01',   'max' => '2014-01-01'),
                array("min" => PDO::PARAM_STR, 'max' => PDO::PARAM_STR),
            ),
        ),
        // or 'conditions' => "created > '2013-01-01' AND created < '2014-01-01'",
        'group'      => array('id', 'name'),
        'having'     => "name = 'Kamil'",
        'order'      => array('name', 'id'),
        'limit'      => 20,
        'offset'     => 20,
        // or 'limit' => array(20, 20),
    );
    $queryBuilder = new Phalcon\Mvc\Model\Query\Builder\Select($params);




public :doc:`Phalcon\\Mvc\\Model\\Query\\Builder\\Select <Phalcon_Mvc_Model_Query_Builder_Select>`  **distinct** (*bool|null* $distinct)

Sets SELECT DISTINCT / SELECT ALL flag



public *bool*  **getDistinct** ()

Returns SELECT DISTINCT / SELECT ALL flag



public :doc:`Phalcon\\Mvc\\Model\\Query\\Builder\\Select <Phalcon_Mvc_Model_Query_Builder_Select>`  **columns** (*string|array* $columns)

Sets the columns to be queried 

.. code-block:: php

    <?php

    $builder->columns(array('id', 'name'));




public *string|array*  **getColumns** ()

Return the columns to be queried



public :doc:`Phalcon\\Mvc\\Model\\Query\\Builder\\Select <Phalcon_Mvc_Model_Query_Builder_Select>`  **from** (*string|array* $models)

Sets the models who makes part of the query 

.. code-block:: php

    <?php

    $builder->from('Robots');
    $builder->from(array('Robots', 'RobotsParts'));




public :doc:`Phalcon\\Mvc\\Model\\Query\\Builder\\Select <Phalcon_Mvc_Model_Query_Builder_Select>`  **addFrom** (*string* $model, [*string* $alias])

Add a model to take part of the query 

.. code-block:: php

    <?php

    $builder->addFrom('Robots', 'r');




public *string|array*  **getFrom** ()

Return the models who makes part of the query



public :doc:`Phalcon\\Mvc\\Model\\Query\\Builder\\Select <Phalcon_Mvc_Model_Query_Builder_Select>`  **orderBy** (*string* $orderBy)

Sets a ORDER BY condition clause 

.. code-block:: php

    <?php

    $builder->orderBy('Robots.name');
    $builder->orderBy(array('1', 'Robots.name'));




public *string|array*  **getOrderBy** ()

Returns the set ORDER BY clause



public :doc:`Phalcon\\Mvc\\Model\\Query\\Builder\\Select <Phalcon_Mvc_Model_Query_Builder_Select>`  **having** (*string* $having)

Sets a HAVING condition clause. You need to escape PHQL reserved words using [ and ] delimiters 

.. code-block:: php

    <?php

    $builder->having('SUM(Robots.price) > 0');




public *string|array*  **getHaving** ()

Return the current having clause



public :doc:`Phalcon\\Mvc\\Model\\Query\\Builder\\Select <Phalcon_Mvc_Model_Query_Builder_Select>`  **limit** (*int* $limit, [*int* $offset])

Sets a LIMIT clause, optionally a offset clause 

.. code-block:: php

    <?php

    $builder->limit(100);
    $builder->limit(100, 20);




public *string|array*  **getLimit** ()

Returns the current LIMIT clause



public :doc:`Phalcon\\Mvc\\Model\\Query\\Builder\\Select <Phalcon_Mvc_Model_Query_Builder_Select>`  **offset** (*int* $offset)

Sets an OFFSET clause 

.. code-block:: php

    <?php

    $builder->offset(30);




public *string|array*  **getOffset** ()

Returns the current OFFSET clause



public :doc:`Phalcon\\Mvc\\Model\\Query\\Builder\\Select <Phalcon_Mvc_Model_Query_Builder_Select>`  **groupBy** (*string* $group)

Sets a GROUP BY clause 

.. code-block:: php

    <?php

    $builder->groupBy(array('Robots.name'));




public *string*  **getGroupBy** ()

Returns the GROUP BY clause



protected *string*  **_compile** ()

Returns a PHQL statement built based on the builder parameters



public :doc:`Phalcon\\Mvc\\Model\\Query\\Builder\\Join <Phalcon_Mvc_Model_Query_Builder_Join>`  **join** (*string* $model, [*string* $conditions], [*string* $alias]) inherited from Phalcon\\Mvc\\Model\\Query\\Builder\\Join

Adds a join to the query 

.. code-block:: php

    <?php

    $builder->join('Robots');
    $builder->join('Robots', 'r.id = RobotsParts.robots_id');
    $builder->join('Robots', 'r.id = RobotsParts.robots_id', 'r');
    $builder->join('Robots', 'r.id = RobotsParts.robots_id', 'r', 'LEFT');




public :doc:`Phalcon\\Mvc\\Model\\Query\\Builder\\Join <Phalcon_Mvc_Model_Query_Builder_Join>`  **innerJoin** (*string* $model, [*string* $conditions], [*string* $alias]) inherited from Phalcon\\Mvc\\Model\\Query\\Builder\\Join

Adds a INNER join to the query 

.. code-block:: php

    <?php

    $builder->innerJoin('Robots');
    $builder->innerJoin('Robots', 'r.id = RobotsParts.robots_id');
    $builder->innerJoin('Robots', 'r.id = RobotsParts.robots_id', 'r');




public :doc:`Phalcon\\Mvc\\Model\\Query\\Builder\\Join <Phalcon_Mvc_Model_Query_Builder_Join>`  **leftJoin** (*string* $model, [*string* $conditions], [*string* $alias]) inherited from Phalcon\\Mvc\\Model\\Query\\Builder\\Join

Adds a LEFT join to the query 

.. code-block:: php

    <?php

    $builder->leftJoin('Robots', 'r.id = RobotsParts.robots_id', 'r');




public :doc:`Phalcon\\Mvc\\Model\\Query\\Builder\\Join <Phalcon_Mvc_Model_Query_Builder_Join>`  **rightJoin** (*string* $model, [*string* $conditions], [*string* $alias]) inherited from Phalcon\\Mvc\\Model\\Query\\Builder\\Join

Adds a RIGHT join to the query 

.. code-block:: php

    <?php

    $builder->rightJoin('Robots', 'r.id = RobotsParts.robots_id', 'r');




public *int*  **setConditions** (*unknown* $conditions) inherited from Phalcon\\Mvc\\Model\\Query\\Builder\\Where

Gets the type of PHQL queries



public *string*  **getConditions** () inherited from Phalcon\\Mvc\\Model\\Query\\Builder\\Where

Returns the conditions, If the conditions is a single numeric field. We internally create a condition using the related primary key 

.. code-block:: php

    <?php

    $builder->getConditions();




public :doc:`Phalcon\\Mvc\\Model\\Query\\Builder <Phalcon_Mvc_Model_Query_Builder>`  **where** (*string* $conditions, [*array* $bindParams], [*array* $bindTypes]) inherited from Phalcon\\Mvc\\Model\\Query\\Builder\\Where

Sets the query conditions 

.. code-block:: php

    <?php

    $builder->where('name = "Peter"');
    $builder->where('name = :name: AND id > :id:', array('name' => 'Peter', 'id' => 100));




public :doc:`Phalcon\\Mvc\\Model\\Query\\Builder <Phalcon_Mvc_Model_Query_Builder>`  **andWhere** (*string* $conditions, [*array* $bindParams], [*array* $bindTypes]) inherited from Phalcon\\Mvc\\Model\\Query\\Builder\\Where

Appends a condition to the current conditions using a AND operator 

.. code-block:: php

    <?php

    $builder->andWhere('name = "Peter"');
    $builder->andWhere('name = :name: AND id > :id:', array('name' => 'Peter', 'id' => 100));




public :doc:`Phalcon\\Mvc\\Model\\Query\\Builder <Phalcon_Mvc_Model_Query_Builder>`  **orWhere** (*string* $conditions, [*array* $bindParams], [*array* $bindTypes]) inherited from Phalcon\\Mvc\\Model\\Query\\Builder\\Where

Appends a condition to the current conditions using a OR operator 

.. code-block:: php

    <?php

    $builder->orWhere('name = "Peter"');
    $builder->orWhere('name = :name: AND id > :id:', array('name' => 'Peter', 'id' => 100));




public :doc:`Phalcon\\Mvc\\Model\\Query\\Builder <Phalcon_Mvc_Model_Query_Builder>`  **betweenWhere** (*string* $expr, *mixed* $minimum, *mixed* $maximum, [*boolean* $useOrWhere]) inherited from Phalcon\\Mvc\\Model\\Query\\Builder\\Where

Appends a BETWEEN condition to the current conditions 

.. code-block:: php

    <?php

    $builder->betweenWhere('price', 100.25, 200.50);




public :doc:`Phalcon\\Mvc\\Model\\Query\\Builder <Phalcon_Mvc_Model_Query_Builder>`  **notBetweenWhere** (*string* $expr, *mixed* $minimum, *mixed* $maximum, [*boolean* $useOrWhere]) inherited from Phalcon\\Mvc\\Model\\Query\\Builder\\Where

Appends a NOT BETWEEN condition to the current conditions 

.. code-block:: php

    <?php

    $builder->notBetweenWhere('price', 100.25, 200.50);




public :doc:`Phalcon\\Mvc\\Model\\Query\\Builder <Phalcon_Mvc_Model_Query_Builder>`  **inWhere** (*string* $expr, *array* $values, [*boolean* $useOrWhere]) inherited from Phalcon\\Mvc\\Model\\Query\\Builder\\Where

Appends an IN condition to the current conditions 

.. code-block:: php

    <?php

    $builder->inWhere('id', [1, 2, 3]);




public :doc:`Phalcon\\Mvc\\Model\\Query\\Builder <Phalcon_Mvc_Model_Query_Builder>`  **notInWhere** (*string* $expr, *array* $values, [*boolean* $useOrWhere]) inherited from Phalcon\\Mvc\\Model\\Query\\Builder\\Where

Appends a NOT IN condition to the current conditions 

.. code-block:: php

    <?php

    $builder->notInWhere('id', [1, 2, 3]);




public *string|array*  **getWhere** () inherited from Phalcon\\Mvc\\Model\\Query\\Builder\\Where

Return the conditions for the query



public static :doc:`Phalcon\\Mvc\\Model\\Query\\Builder <Phalcon_Mvc_Model_Query_Builder>`  **create** (*unknown* $type) inherited from Phalcon\\Mvc\\Model\\Query\\Builder

Create a new Query Builder of the given type. 

.. code-block:: php

    <?php

    Phalcon\Mvc\Model\Query\Builder::create(Phalcon\Mvc\Model\Query::TYPE_SELECT);




public static :doc:`Phalcon\\Mvc\\Model\\Query\\Builder\\Select <Phalcon_Mvc_Model_Query_Builder_Select>`  **createSelectBuilder** () inherited from Phalcon\\Mvc\\Model\\Query\\Builder

Create a new Query Builder for Select



public static :doc:`Phalcon\\Mvc\\Model\\Query\\Builder\\Insert <Phalcon_Mvc_Model_Query_Builder_Insert>`  **createInsertBuilder** () inherited from Phalcon\\Mvc\\Model\\Query\\Builder

Create a new Query Builder for Insert



public static :doc:`Phalcon\\Mvc\\Model\\Query\\Builder\\Update <Phalcon_Mvc_Model_Query_Builder_Update>`  **createUpdateBuilder** () inherited from Phalcon\\Mvc\\Model\\Query\\Builder

Create a new Query Builder for Update



public static :doc:`Phalcon\\Mvc\\Model\\Query\\Builder\\Delete <Phalcon_Mvc_Model_Query_Builder_Delete>`  **createDeleteBuilder** () inherited from Phalcon\\Mvc\\Model\\Query\\Builder

Create a new Query Builder for Delete



public *int*  **getType** () inherited from Phalcon\\Mvc\\Model\\Query\\Builder

Gets the type of PHQL queries



public :doc:`Phalcon\\Mvc\\Model\\Query\\Builder <Phalcon_Mvc_Model_Query_Builder>`  **setBindParams** (*unknown* $bindparams, [*unknown* $merge]) inherited from Phalcon\\Mvc\\Model\\Query\\Builder

Sets the bind parameters



public :doc:`Phalcon\\Mvc\\Model\\Query\\Builder <Phalcon_Mvc_Model_Query_Builder>`  **getBindParams** () inherited from Phalcon\\Mvc\\Model\\Query\\Builder

Gets the bind parameters



public :doc:`Phalcon\\Mvc\\Model\\Query\\Builder <Phalcon_Mvc_Model_Query_Builder>`  **getMergeBindParams** () inherited from Phalcon\\Mvc\\Model\\Query\\Builder

Gets the merge bind parameters



public :doc:`Phalcon\\Mvc\\Model\\Query\\Builder <Phalcon_Mvc_Model_Query_Builder>`  **setBindTypes** (*unknown* $bindtypes, [*unknown* $merge]) inherited from Phalcon\\Mvc\\Model\\Query\\Builder

Sets the bind types



public :doc:`Phalcon\\Mvc\\Model\\Query\\Builder <Phalcon_Mvc_Model_Query_Builder>`  **getBindTypes** () inherited from Phalcon\\Mvc\\Model\\Query\\Builder

Gets the bind types



public :doc:`Phalcon\\Mvc\\Model\\Query\\Builder <Phalcon_Mvc_Model_Query_Builder>`  **getMergeBindTypes** () inherited from Phalcon\\Mvc\\Model\\Query\\Builder

Gets the merge bind types



public :doc:`Phalcon\\Mvc\\Model\\Query\\Builder <Phalcon_Mvc_Model_Query_Builder>`  **compile** () inherited from Phalcon\\Mvc\\Model\\Query\\Builder

Compile the PHQL query



public *string*  **getPhql** () inherited from Phalcon\\Mvc\\Model\\Query\\Builder

Returns a PHQL statement built based on the builder parameters



public :doc:`Phalcon\\Mvc\\Model\\Query <Phalcon_Mvc_Model_Query>`  **getQuery** () inherited from Phalcon\\Mvc\\Model\\Query\\Builder

Returns the query built



public  **setDI** (:doc:`Phalcon\\DiInterface <Phalcon_DiInterface>` $dependencyInjector) inherited from Phalcon\\DI\\Injectable

Sets the dependency injector



public :doc:`Phalcon\\DiInterface <Phalcon_DiInterface>`  **getDI** ([*unknown* $error]) inherited from Phalcon\\DI\\Injectable

Returns the internal dependency injector



public  **setEventsManager** (:doc:`Phalcon\\Events\\ManagerInterface <Phalcon_Events_ManagerInterface>` $eventsManager) inherited from Phalcon\\DI\\Injectable

Sets the event manager



public :doc:`Phalcon\\Events\\ManagerInterface <Phalcon_Events_ManagerInterface>`  **getEventsManager** () inherited from Phalcon\\DI\\Injectable

Returns the internal event manager



public *boolean*  **fireEvent** (*string* $eventName, [*unknown* $data], [*unknown* $cancelable]) inherited from Phalcon\\DI\\Injectable

Fires an event, implicitly calls behaviors and listeners in the events manager are notified



public *boolean*  **fireEventCancel** (*string* $eventName, [*unknown* $data], [*unknown* $cancelable]) inherited from Phalcon\\DI\\Injectable

Fires an event, implicitly calls behaviors and listeners in the events manager are notified This method stops if one of the callbacks/listeners returns boolean false



public *boolean*  **hasService** (*string* $name) inherited from Phalcon\\DI\\Injectable

Check whether the DI contains a service by a name



public *mixed*  **getResolveService** (*string* $name, [*unknown* $args], [*unknown* $noerror], [*unknown* $noshared]) inherited from Phalcon\\DI\\Injectable

Resolves the service based on its configuration



public  **__get** (*unknown* $property) inherited from Phalcon\\DI\\Injectable

Magic method __get



public  **__sleep** () inherited from Phalcon\\DI\\Injectable

...


public  **__debugInfo** () inherited from Phalcon\\DI\\Injectable

...


