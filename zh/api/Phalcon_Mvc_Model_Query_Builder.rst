Abstract class **Phalcon\\Mvc\\Model\\Query\\Builder**
======================================================

*extends* abstract class :doc:`Phalcon\\Di\\Injectable <Phalcon_Di_Injectable>`

*implements* :doc:`Phalcon\\Events\\EventsAwareInterface <Phalcon_Events_EventsAwareInterface>`, :doc:`Phalcon\\Di\\InjectionAwareInterface <Phalcon_Di_InjectionAwareInterface>`, :doc:`Phalcon\\Mvc\\Model\\Query\\BuilderInterface <Phalcon_Mvc_Model_Query_BuilderInterface>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/mvc/model/query/builder.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Helps to create PHQL queries using an OO interface  

.. code-block:: php

    <?php

    $resultset = Phalcon\Mvc\Model\Query\Builder::create(Phalcon\Mvc\Model\Query::TYPE_SELECT)
       ->from('Robots')
       ->join('RobotsParts')
       ->limit(20)
       ->orderBy('Robots.name')
       ->getQuery()
       ->execute();



Methods
-------

public static :doc:`Phalcon\\Mvc\\Model\\Query\\Builder <Phalcon_Mvc_Model_Query_Builder>`  **create** (*unknown* $type)

Create a new Query Builder of the given type. 

.. code-block:: php

    <?php

    Phalcon\Mvc\Model\Query\Builder::create(Phalcon\Mvc\Model\Query::TYPE_SELECT);




public static :doc:`Phalcon\\Mvc\\Model\\Query\\Builder\\Select <Phalcon_Mvc_Model_Query_Builder_Select>`  **createSelectBuilder** ([*array* $params], [:doc:`Phalcon\\DiInterface <Phalcon_DiInterface>` $dependencyInjector])

Create a new Query Builder for Select



public static :doc:`Phalcon\\Mvc\\Model\\Query\\Builder\\Insert <Phalcon_Mvc_Model_Query_Builder_Insert>`  **createInsertBuilder** ([*array* $params], [:doc:`Phalcon\\DiInterface <Phalcon_DiInterface>` $dependencyInjector])

Create a new Query Builder for Insert



public static :doc:`Phalcon\\Mvc\\Model\\Query\\Builder\\Update <Phalcon_Mvc_Model_Query_Builder_Update>`  **createUpdateBuilder** ([*array* $params], [:doc:`Phalcon\\DiInterface <Phalcon_DiInterface>` $dependencyInjector])

Create a new Query Builder for Update



public static :doc:`Phalcon\\Mvc\\Model\\Query\\Builder\\Delete <Phalcon_Mvc_Model_Query_Builder_Delete>`  **createDeleteBuilder** ([*array* $params], [:doc:`Phalcon\\DiInterface <Phalcon_DiInterface>` $dependencyInjector])

Create a new Query Builder for Delete



public *int*  **getType** ()

Gets the type of PHQL queries



public :doc:`Phalcon\\Mvc\\Model\\Query\\Builder <Phalcon_Mvc_Model_Query_Builder>`  **setBindParams** (*array* $bindparams, [*unknown* $merge])

Sets the bind parameters



public :doc:`Phalcon\\Mvc\\Model\\Query\\Builder <Phalcon_Mvc_Model_Query_Builder>`  **getBindParams** ()

Gets the bind parameters



public :doc:`Phalcon\\Mvc\\Model\\Query\\Builder <Phalcon_Mvc_Model_Query_Builder>`  **getMergeBindParams** ()

Gets the merge bind parameters



public :doc:`Phalcon\\Mvc\\Model\\Query\\Builder <Phalcon_Mvc_Model_Query_Builder>`  **setBindTypes** (*array* $bindtypes, [*unknown* $merge])

Sets the bind types



public :doc:`Phalcon\\Mvc\\Model\\Query\\Builder <Phalcon_Mvc_Model_Query_Builder>`  **getBindTypes** ()

Gets the bind types



public :doc:`Phalcon\\Mvc\\Model\\Query\\Builder <Phalcon_Mvc_Model_Query_Builder>`  **getMergeBindTypes** ()

Gets the merge bind types



public :doc:`Phalcon\\Mvc\\Model\\Query\\Builder <Phalcon_Mvc_Model_Query_Builder>`  **compile** ()

Compile the PHQL query



public *string*  **getPhql** ()

Returns a PHQL statement built based on the builder parameters



public :doc:`Phalcon\\Mvc\\Model\\Query <Phalcon_Mvc_Model_Query>`  **getQuery** ()

Returns the query built



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


