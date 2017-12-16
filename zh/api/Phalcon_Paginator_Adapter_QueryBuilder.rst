Class **Phalcon\\Paginator\\Adapter\\QueryBuilder**
===================================================

*extends* abstract class :doc:`Phalcon\\Paginator\\Adapter <Phalcon_Paginator_Adapter>`

*implements* :doc:`Phalcon\\Paginator\\AdapterInterface <Phalcon_Paginator_AdapterInterface>`, :doc:`Phalcon\\Di\\InjectionAwareInterface <Phalcon_Di_InjectionAwareInterface>`, :doc:`Phalcon\\Events\\EventsAwareInterface <Phalcon_Events_EventsAwareInterface>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/paginator/adapter/querybuilder.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Pagination using a PHQL query builder as source of data  

.. code-block:: php

    <?php

      $builder = $this->modelsManager->createBuilder()
                       ->columns('id, name')
                       ->from('Robots')
                       ->orderBy('name');
    
      $paginator = new Phalcon\Paginator\Adapter\QueryBuilder(array(
          "builder" => $builder,
          "limit"=> 20,
          "page" => 1
      ));



Methods
-------

public  **__construct** (*array* $config)





public *\stdClass*  **getPaginate** ()

Returns a slice of the resultset to show in the pagination



public :doc:`Phalcon\\Paginator\\Adapter\\QueryBuilder <Phalcon_Paginator_Adapter_QueryBuilder>`  $this Fluent interface **setQueryBuilder** (*unknown* $queryBuilder)

Set query builder object



public :doc:`Phalcon\\Mvc\\Model\\Query\\BuilderInterface <Phalcon_Mvc_Model_Query_BuilderInterface>`  $builder **getQueryBuilder** ()

Get query builder object



public  **setCurrentPage** (*int* $page) inherited from Phalcon\\Paginator\\Adapter

Set current page number



public  **getCurrentPage** () inherited from Phalcon\\Paginator\\Adapter

Get current page number



public :doc:`Phalcon\\Paginator\\Adapter <Phalcon_Paginator_Adapter>`  **setLimit** (*int* $limit) inherited from Phalcon\\Paginator\\Adapter

Set current rows limit



public *int $limit*  **getLimit** () inherited from Phalcon\\Paginator\\Adapter

Get current rows limit



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


