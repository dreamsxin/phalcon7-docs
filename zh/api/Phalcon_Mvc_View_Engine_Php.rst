Class **Phalcon\\Mvc\\View\\Engine\\Php**
=========================================

*extends* abstract class :doc:`Phalcon\\Mvc\\View\\Engine <Phalcon_Mvc_View_Engine>`

*implements* :doc:`Phalcon\\Mvc\\View\\EngineInterface <Phalcon_Mvc_View_EngineInterface>`, :doc:`Phalcon\\DI\\InjectionAwareInterface <Phalcon_DI_InjectionAwareInterface>`, :doc:`Phalcon\\Events\\EventsAwareInterface <Phalcon_Events_EventsAwareInterface>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/mvc/view/engine/php.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Adapter to use PHP itself as templating engine


Methods
-------

public  **render** (*string* $path, *array* $params, [*boolean* $mustClean])

Renders a view using the template engine



public  **__construct** (:doc:`Phalcon\\Mvc\\ViewInterface <Phalcon_Mvc_ViewInterface>` $view, [:doc:`Phalcon\\DiInterface <Phalcon_DiInterface>` $dependencyInjector]) inherited from Phalcon\\Mvc\\View\\Engine

Phalcon\\Mvc\\View\\Engine constructor



public *array*  **getContent** () inherited from Phalcon\\Mvc\\View\\Engine

Returns cached ouput on another view stage



public  **startSection** (*string* $name) inherited from Phalcon\\Mvc\\View\\Engine

Start a new section block



public *string*  **stopSection** () inherited from Phalcon\\Mvc\\View\\Engine

Stop the current section block



public *string|null*  **section** (*string* $name, [*unknown* $defaultValue]) inherited from Phalcon\\Mvc\\View\\Engine

Returns the content for a section block



public *string*  **partial** (*string* $partialPath) inherited from Phalcon\\Mvc\\View\\Engine

Renders a partial inside another view



public :doc:`Phalcon\\Mvc\\ViewInterface <Phalcon_Mvc_ViewInterface>`  **getView** () inherited from Phalcon\\Mvc\\View\\Engine

Returns the view component related to the adapter



public :doc:`Phalcon\\Mvc\\View\\Engine <Phalcon_Mvc_View_Engine>`  **addMethod** (*string* $name, *unknown* $handler) inherited from Phalcon\\Mvc\\View\\Engine

Adds a user-defined method



public *mixed*  **__call** (*string* $method, [*array* $arguments]) inherited from Phalcon\\Mvc\\View\\Engine

Handles method calls when a method is not implemented



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


