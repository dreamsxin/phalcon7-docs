Abstract class **Phalcon\\Db\\Builder\\Join**
=============================================

*extends* abstract class :doc:`Phalcon\\Db\\Builder\\Where <Phalcon_Db_Builder_Where>`

*implements* :doc:`Phalcon\\Events\\EventsAwareInterface <Phalcon_Events_EventsAwareInterface>`, :doc:`Phalcon\\Di\\InjectionAwareInterface <Phalcon_Di_InjectionAwareInterface>`, :doc:`Phalcon\\Db\\BuilderInterface <Phalcon_Db_BuilderInterface>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/db/builder/join.c" class="btn btn-default btn-sm">Source on GitHub</a>`




Constants
---------

*string* **LEFT**

*string* **RIGHT**

*string* **INNER**

Methods
-------

public :doc:`Phalcon\\Db\\Builder\\Join <Phalcon_Db_Builder_Join>`  **join** (*string* $table, [*string* $conditions], [*string* $type])

Adds a join to the query



public :doc:`Phalcon\\Db\\Builder\\Join <Phalcon_Db_Builder_Join>`  **innerJoin** (*string* $table, [*string* $conditions])

Adds a INNER join to the query



public :doc:`Phalcon\\Db\\Builder\\Join <Phalcon_Db_Builder_Join>`  **leftJoin** (*string* $table, [*string* $conditions])

Adds a LEFT join to the query



public :doc:`Phalcon\\Db\\Builder\\Join <Phalcon_Db_Builder_Join>`  **rightJoin** (*string* $table, [*string* $conditions])

Adds a RIGHT join to the query



public *int*  **setConditions** (*string|array* $conditions, [*array* $bindParams], [*array* $bindTypes], [*array* $bindParams], [*boolean* $type]) inherited from Phalcon\\Db\\Builder\\Where

Gets the type of PHQL queries



public *string*  **getConditions** () inherited from Phalcon\\Db\\Builder\\Where

Return the conditions



public :doc:`Phalcon\\Db\\Builder <Phalcon_Db_Builder>`  **where** (*string* $conditions, [*array* $bindParams], [*array* $bindTypes]) inherited from Phalcon\\Db\\Builder\\Where

Sets the query conditions 

.. code-block:: php

    <?php

    $builder->where('name = "Peter"');
    $builder->where('name = :name AND id > :id', array('name' => 'Peter', 'id' => 100));




public :doc:`Phalcon\\Db\\Builder <Phalcon_Db_Builder>`  **andWhere** (*string* $conditions, [*array* $bindParams], [*array* $bindTypes]) inherited from Phalcon\\Db\\Builder\\Where

Appends a condition to the current conditions using a AND operator 

.. code-block:: php

    <?php

    $builder->andWhere('name = "Peter"');
    $builder->andWhere('name = :name AND id > :id', array('name' => 'Peter', 'id' => 100));




public :doc:`Phalcon\\Db\\Builder <Phalcon_Db_Builder>`  **orWhere** (*string* $conditions, [*array* $bindParams], [*array* $bindTypes]) inherited from Phalcon\\Db\\Builder\\Where

Appends a condition to the current conditions using a OR operator



public :doc:`Phalcon\\Db\\Builder <Phalcon_Db_Builder>`  **inWhere** (*string* $expr, *array* $values, [*boolean* $useOrWhere]) inherited from Phalcon\\Db\\Builder\\Where

Appends an IN condition to the current conditions



public :doc:`Phalcon\\Db\\Builder <Phalcon_Db_Builder>`  **notInWhere** (*string* $expr, *array* $values, [*boolean* $useOrWhere]) inherited from Phalcon\\Db\\Builder\\Where

Appends a NOT IN condition to the current conditions



public static :doc:`Phalcon\\Db\\Builder\\Select <Phalcon_Db_Builder_Select>`  **select** (*unknown* $tables, [*unknown* $db]) inherited from Phalcon\\Db\\Builder

Create a select builder 

.. code-block:: php

    <?php

     $resultset = Phalcon\Db\Builder::select('robots')
     	  ->join('robots_parts', 'robots.id = robots_parts.robots_id')
     	  ->where('robots.id = 1')
     	  ->limit(20)
     	  ->orderBy('robots.name')
        ->execute();




public static :doc:`Phalcon\\Db\\Builder\\Update <Phalcon_Db_Builder_Update>`  **update** (*unknown* $table, [*unknown* $db]) inherited from Phalcon\\Db\\Builder

Create a update builder 

.. code-block:: php

    <?php

     $ret = Phalcon\Db\Builder::update('robots')
     	  ->set(['name' => 'test'])
     	  ->where('id = 1')
        ->execute();




public static :doc:`Phalcon\\Db\\Builder\\Insert <Phalcon_Db_Builder_Insert>`  **insert** (*unknown* $table, [*unknown* $db]) inherited from Phalcon\\Db\\Builder

Create a insert builder 

.. code-block:: php

    <?php

     $ret = Phalcon\Db\Builder::insert('robots')
     	  ->values(['name' => 'test'])
        ->execute();




public static :doc:`Phalcon\\Db\\Builder\\Delete <Phalcon_Db_Builder_Delete>`  **delete** (*unknown* $table, [*unknown* $db]) inherited from Phalcon\\Db\\Builder

Create a delete builder 

.. code-block:: php

    <?php

     $ret = Phalcon\Db\Builder::delete('robots')
     	  ->where('id = 1')
        ->execute();




public :doc:`Phalcon\\Db\\Builder <Phalcon_Db_Builder>`  **setBindParams** (*array* $bindparams, [*unknown* $merge]) inherited from Phalcon\\Db\\Builder

Sets the bind parameters



public :doc:`Phalcon\\Db\\Builder <Phalcon_Db_Builder>`  **getBindParams** () inherited from Phalcon\\Db\\Builder

Gets the bind parameters



public :doc:`Phalcon\\Db\\Builder <Phalcon_Db_Builder>`  **setBindTypes** (*array* $bindtypes, [*unknown* $merge]) inherited from Phalcon\\Db\\Builder

Sets the bind types



public :doc:`Phalcon\\Db\\Builder <Phalcon_Db_Builder>`  **getBindTypes** () inherited from Phalcon\\Db\\Builder

Gets the bind types



public :doc:`Phalcon\\Db\\ResultInterface <Phalcon_Db_ResultInterface>` |boolean **execute** () inherited from Phalcon\\Db\\Builder

Execute query



public  **setDI** (:doc:`Phalcon\\DiInterface <Phalcon_DiInterface>` $dependencyInjector) inherited from Phalcon\\Di\\Injectable

Sets the dependency injector



public :doc:`Phalcon\\DiInterface <Phalcon_DiInterface>`  **getDI** ([*unknown* $error], [*unknown* $notUseDefault]) inherited from Phalcon\\Di\\Injectable

Returns the internal dependency injector



public  **setEventsManager** (:doc:`Phalcon\\Events\\ManagerInterface <Phalcon_Events_ManagerInterface>` $eventsManager) inherited from Phalcon\\Di\\Injectable

Sets the event manager



public :doc:`Phalcon\\Events\\ManagerInterface <Phalcon_Events_ManagerInterface>`  **getEventsManager** () inherited from Phalcon\\Di\\Injectable

Returns the internal event manager



public *boolean*  **fireEvent** (*string* $eventName, [*mixed* $data], [*unknown* $cancelable]) inherited from Phalcon\\Di\\Injectable

Fires an event, implicitly calls behaviors and listeners in the events manager are notified



public *mixed*  **fireEventCancel** (*string* $eventName, [*mixed* $data], [*unknown* $cancelable]) inherited from Phalcon\\Di\\Injectable

Fires an event, can stop the event by returning to the false



public *boolean*  **hasService** (*string* $name) inherited from Phalcon\\Di\\Injectable

Check whether the DI contains a service by a name



public :doc:`Phalcon\\Di\\ServiceInterface <Phalcon_Di_ServiceInterface>`  **setService** (*unknown* $name) inherited from Phalcon\\Di\\Injectable

Sets a service from the DI



public *object|null*  **getService** (*unknown* $name) inherited from Phalcon\\Di\\Injectable

Obtains a service from the DI



public *mixed*  **getResolveService** (*string* $name, [*array* $args], [*unknown* $noerror], [*unknown* $noshared]) inherited from Phalcon\\Di\\Injectable

Resolves the service based on its configuration



public  **attachEvent** (*string* $eventType, *Closure* $callback) inherited from Phalcon\\Di\\Injectable

Attach a listener to the events



public  **__get** (*unknown* $property) inherited from Phalcon\\Di\\Injectable

Magic method __get



public  **__sleep** () inherited from Phalcon\\Di\\Injectable

...


public  **__debugInfo** () inherited from Phalcon\\Di\\Injectable

...


