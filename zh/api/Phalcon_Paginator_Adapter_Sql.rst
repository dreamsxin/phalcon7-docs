Class **Phalcon\\Paginator\\Adapter\\Sql**
==========================================

*extends* abstract class :doc:`Phalcon\\Di\\Injectable <Phalcon_Di_Injectable>`

*implements* :doc:`Phalcon\\Events\\EventsAwareInterface <Phalcon_Events_EventsAwareInterface>`, :doc:`Phalcon\\Di\\InjectionAwareInterface <Phalcon_Di_InjectionAwareInterface>`, :doc:`Phalcon\\Paginator\\AdapterInterface <Phalcon_Paginator_AdapterInterface>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/paginator/adapter/sql.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Pagination using a SQL as source of data  

.. code-block:: php

    <?php

     $sql = "SELECT * FROM robots WHERE type = :type LIMIT :limit OFFSET :offset";
     $sql2 = "SELECT COUNT(*) rowcount FROM robots WHERE type = :type FROM robots";
    
     $bind = ['type' => 'google'];
    
     $paginator = new \Phalcon\Paginator\Adapter\Sql(array(
                     "db" => $this->db,
                     "sql" => $sql,
                     "total_sql" => $sql2,
                     "bind" => $bind,
                     "limit" => 20,
                     "page" => $page
     ));



Methods
-------

public  **__construct** (*array* $config)





public *stdClass*  **getPaginate** ()

Returns a slice of the resultset to show in the pagination



public :doc:`Phalcon\\Paginator\\Adapter\\Sql <Phalcon_Paginator_Adapter_Sql>`  $this Fluent interface **setLimit** (*int* $limit)

Set current rows limit



public *int $limit*  **getLimit** ()

Get current rows limit



public  **setCurrentPage** (*int* $page)

Set current page number



public  **getCurrentPage** ()

Get current page number



public :doc:`Phalcon\\Paginator\\Adapter\\Sql <Phalcon_Paginator_Adapter_Sql>`  $this Fluent interface **setDb** (:doc:`Phalcon\\Db\\AdapterInterface <Phalcon_Db_AdapterInterface>` $db)

Set query builder object



public :doc:`Phalcon\\Db\\AdapterInterface <Phalcon_Db_AdapterInterface>`  $db **getDb** ()

Get query builder object



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



public *boolean*  **hasService** (*string* $name) inherited from Phalcon\\Di\\Injectable

Check whether the DI contains a service by a name



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


