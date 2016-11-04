Abstract class **Phalcon\\Mvc\\Controller**
===========================================

*extends* abstract class :doc:`Phalcon\\DI\\Injectable <Phalcon_DI_Injectable>`

*implements* :doc:`Phalcon\\Events\\EventsAwareInterface <Phalcon_Events_EventsAwareInterface>`, :doc:`Phalcon\\DI\\InjectionAwareInterface <Phalcon_DI_InjectionAwareInterface>`, :doc:`Phalcon\\Mvc\\ControllerInterface <Phalcon_Mvc_ControllerInterface>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/mvc/controller.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Every application controller should extend this class that encapsulates all the controller functionality  The controllers provide the “flow” between models and views. Controllers are responsible for processing the incoming requests from the web browser, interrogating the models for data, and passing that data on to the views for presentation.  

.. code-block:: php

    <?php

    class PeopleController extends \Phalcon\Mvc\Controller
    {
    
      //This action will be executed by default
      public function indexAction()
      {
    
      }
    
      public function findAction()
      {
    
      }
    
      public function saveAction()
      {
       //Forwards flow to the index action
       return $this->dispatcher->forward(array('controller' => 'people', 'action' => 'index'));
      }
    
    }



Methods
-------

final public  **__construct** ()

Phalcon\\Mvc\\Controller constructor



public  **setDI** (:doc:`Phalcon\\DIInterface <Phalcon_DIInterface>` $dependencyInjector) inherited from Phalcon\\DI\\Injectable

Sets the dependency injector



public :doc:`Phalcon\\DIInterface <Phalcon_DIInterface>`  **getDI** ([*unknown* $error], [*unknown* $notUseDefault]) inherited from Phalcon\\DI\\Injectable

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


