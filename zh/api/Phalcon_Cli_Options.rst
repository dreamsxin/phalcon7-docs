Class **Phalcon\\Cli\\Options**
===============================

*extends* abstract class :doc:`Phalcon\\Di\\Injectable <Phalcon_Di_Injectable>`

*implements* :doc:`Phalcon\\Events\\EventsAwareInterface <Phalcon_Events_EventsAwareInterface>`, :doc:`Phalcon\\Di\\InjectionAwareInterface <Phalcon_Di_InjectionAwareInterface>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/cli/options.c" class="btn btn-default btn-sm">Source on GitHub</a>`


.. code-block:: php

    <?php

     $ops = new \Phalcon\Cli\Options('Phalcon CLI');
      $ops->add([
     	'type' => \Phalcon\Cli\Options::TYPE_INT,
     	'name' => 'min'
     ]);
      $ops->add([
     	'type' => \Phalcon\Cli\Options::TYPE_INT,
     	'name' => 'max',
     	'shortName' => 'm',
     	'required' => false,
     	'desc' => "int",
     	'help' => "must be int",
     	'defaultValue' => 1
     ]);
     $ops->add(\Phalcon\Cli\Options::TYPE_STRING, 'name', 'n', true, "name", "must be string", "Phalcon");
     $values = $ops->parse();



Constants
---------

*integer* **TYPE_INT**

*integer* **TYPE_FLOAT**

*integer* **TYPE_BOOLEAN**

*integer* **TYPE_STRING**

*integer* **TYPE_ARRAY**

Methods
-------

public  **__construct** ([*unknown* $title], [*unknown* $program], [*unknown* $argString], [*unknown* $desc], [*unknown* $dependencyInjector])

Phalcon\\Cli\\Options constructor



public  **add** (*unknown* $arg, [*unknown* $name], [*unknown* $shortname], [*unknown* $required], [*unknown* $desc], [*unknown* $help], [*unknown* $defaultValue])

Add option



public  **help** ()

Print help



public  **parse** ([*array* $options])

Parse and return values



public  **addOption** (*unknown* $arg, [*unknown* $name], [*unknown* $shortname], [*unknown* $required], [*unknown* $desc], [*unknown* $help], [*unknown* $defaultValue])

...


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


