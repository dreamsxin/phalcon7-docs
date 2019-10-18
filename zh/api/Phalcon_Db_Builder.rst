Abstract class **Phalcon\\Db\\Builder**
=======================================

*extends* abstract class :doc:`Phalcon\\Di\\Injectable <Phalcon_Di_Injectable>`

*implements* :doc:`Phalcon\\Events\\EventsAwareInterface <Phalcon_Events_EventsAwareInterface>`, :doc:`Phalcon\\Di\\InjectionAwareInterface <Phalcon_Di_InjectionAwareInterface>`, :doc:`Phalcon\\Db\\BuilderInterface <Phalcon_Db_BuilderInterface>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/db/builder.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Helps to create queries using an OO interface


Methods
-------

public static :doc:`Phalcon\\Db\\Builder\\Select <Phalcon_Db_Builder_Select>`  **select** (*unknown* $tables, [*unknown* $db])

Create a select builder 

.. code-block:: php

    <?php

     $resultset = Phalcon\Db\Builder::select('robots')
     	  ->join('robots_parts', 'robots.id = robots_parts.robots_id')
     	  ->where('robots.id = 1')
     	  ->limit(20)
     	  ->orderBy('robots.name')
        ->execute();




public static :doc:`Phalcon\\Db\\Builder\\Update <Phalcon_Db_Builder_Update>`  **update** (*unknown* $table, [*unknown* $db])

Create a update builder 

.. code-block:: php

    <?php

     $ret = Phalcon\Db\Builder::update('robots')
     	  ->set(['name' => 'test'])
     	  ->where('id = 1')
        ->execute();




public static :doc:`Phalcon\\Db\\Builder\\Insert <Phalcon_Db_Builder_Insert>`  **insert** (*unknown* $table, [*unknown* $db])

Create a insert builder 

.. code-block:: php

    <?php

     $ret = Phalcon\Db\Builder::insert('robots')
     	  ->values(['name' => 'test'])
        ->execute();




public static :doc:`Phalcon\\Db\\Builder\\Delete <Phalcon_Db_Builder_Delete>`  **delete** (*unknown* $table, [*unknown* $db])

Create a delete builder 

.. code-block:: php

    <?php

     $ret = Phalcon\Db\Builder::delete('robots')
     	  ->where('id = 1')
        ->execute();




public :doc:`Phalcon\\Db\\Builder <Phalcon_Db_Builder>`  **setBindParams** (*array* $bindparams, [*unknown* $merge])

Sets the bind parameters



public :doc:`Phalcon\\Db\\Builder <Phalcon_Db_Builder>`  **getBindParams** ()

Gets the bind parameters



public :doc:`Phalcon\\Db\\Builder <Phalcon_Db_Builder>`  **setBindTypes** (*array* $bindtypes, [*unknown* $merge])

Sets the bind types



public :doc:`Phalcon\\Db\\Builder <Phalcon_Db_Builder>`  **getBindTypes** ()

Gets the bind types



public :doc:`Phalcon\\Db\\ResultInterface <Phalcon_Db_ResultInterface>` |boolean|array **execute** ([*unknown* $pretreatment])

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


