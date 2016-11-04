Abstract class **Phalcon\\Dispatcher**
======================================

*extends* abstract class :doc:`Phalcon\\DI\\Injectable <Phalcon_DI_Injectable>`

*implements* :doc:`Phalcon\\Events\\EventsAwareInterface <Phalcon_Events_EventsAwareInterface>`, :doc:`Phalcon\\DI\\InjectionAwareInterface <Phalcon_DI_InjectionAwareInterface>`, :doc:`Phalcon\\DispatcherInterface <Phalcon_DispatcherInterface>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/dispatcher.c" class="btn btn-default btn-sm">Source on GitHub</a>`

This is the base class for Phalcon\\Mvc\\Dispatcher and Phalcon\\CLI\\Dispatcher. This class can't be instantiated directly, you can use it to create your own dispatchers


Constants
---------

*integer* **EXCEPTION_NO_DI**

*integer* **EXCEPTION_CYCLIC_ROUTING**

*integer* **EXCEPTION_HANDLER_NOT_FOUND**

*integer* **EXCEPTION_INVALID_HANDLER**

*integer* **EXCEPTION_INVALID_PARAMS**

*integer* **EXCEPTION_ACTION_NOT_FOUND**

Methods
-------

public  **__construct** ()

Phalcon\\Dispatcher constructor



public  **setActionSuffix** (*string* $actionSuffix)

Sets the default action suffix



public  **setModuleName** (*string* $moduleName)

Sets the module where the controller is (only informative)



public *string*  **getModuleName** ()

Gets the module where the controller class is



public  **setNamespaceName** (*string* $namespaceName)

Sets the namespace where the controller class is



public *string*  **getNamespaceName** ()

Gets a namespace to be prepended to the current handler name



public  **setDefaultNamespace** (*string* $namespace)

Sets the default namespace



public *string*  **getDefaultNamespace** ()

Returns the default namespace



public  **setDefaultAction** (*string* $actionName)

Sets the default action name



public  **setActionName** (*string* $actionName)

Sets the action name to be dispatched



public *string*  **getActionName** ()

Gets the lastest dispatched action name



public  **setLogicBinding** (*boolean* $value)

Enable/Disable logic binding during dispatch



public *boolean*  **isLogicBinding** ()

Check if logic binding



public  **setParams** (*array* $params)

Sets action params to be dispatched



public *array*  **getParams** ()

Gets action params



public  **setParam** (*mixed* $param, *mixed* $value)

Set a param by its name or numeric index



public *mixed*  **getParam** (*mixed* $param, [*string|array* $filters])

Gets a param by its name or numeric index



public *string*  **getActiveMethod** ()

Returns the current method to be/executed in the dispatcher



public *boolean*  **isFinished** ()

Checks if the dispatch loop is finished or has more pendent controllers/tasks to disptach



public  **setFinished** (*boolean* $finished)

Sets the finished



public  **setReturnedValue** (*mixed* $value)

Sets the latest returned value by an action manually



public *mixed*  **getReturnedValue** ()

Returns value returned by the lastest dispatched action



public *object*  **dispatch** ()

Dispatches a handle action taking into account the routing parameters



public *bool*  **forward** (*string|array* $forward)

Forwards the execution flow to another controller/action Dispatchers are unique per module. Forwarding between modules is not allowed 

.. code-block:: php

    <?php

      $this->dispatcher->forward(array('controller' => 'posts', 'action' => 'index'));




public *boolean*  **wasForwarded** ()

Check if the current executed action was forwarded by another one



public *string*  **getHandlerClass** ()

Possible class name that will be located to dispatch the request



public  **camelizeNamespace** (*bool* $camelize)

Enables/Disables automatically camelize namespace  

.. code-block:: php

    <?php

      $this->dispatcher->camelizeNamespace(FALSE);




public  **camelizeController** (*bool* $camelize)

Enables/Disables automatically camelize controller  

.. code-block:: php

    <?php

      $this->dispatcher->camelizeController(FALSE);




public :doc:`Phalcon\\DispatcherInterface <Phalcon_DispatcherInterface>`  **setErrorHandler** (*unknown* $callback, [*int* $exception_code])

Set error handler



public *mixed*  **getErrorHandler** (*int* $exception_code)

Get error handler



public *boolean*  **fireEvent** (*string* $eventName, [*string* $data], [*string* $cancelable])

Fires an event, implicitly calls behaviors and listeners in the events manager are notified



public  **setDI** (:doc:`Phalcon\\DiInterface <Phalcon_DiInterface>` $dependencyInjector) inherited from Phalcon\\DI\\Injectable

Sets the dependency injector



public :doc:`Phalcon\\DiInterface <Phalcon_DiInterface>`  **getDI** ([*unknown* $error], [*unknown* $notUseDefault]) inherited from Phalcon\\DI\\Injectable

Returns the internal dependency injector



public  **setEventsManager** (:doc:`Phalcon\\Events\\ManagerInterface <Phalcon_Events_ManagerInterface>` $eventsManager) inherited from Phalcon\\DI\\Injectable

Sets the event manager



public :doc:`Phalcon\\Events\\ManagerInterface <Phalcon_Events_ManagerInterface>`  **getEventsManager** () inherited from Phalcon\\DI\\Injectable

Returns the internal event manager



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


