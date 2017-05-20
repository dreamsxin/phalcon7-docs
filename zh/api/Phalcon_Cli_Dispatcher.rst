Class **Phalcon\\Cli\\Dispatcher**
==================================

*extends* abstract class :doc:`Phalcon\\Dispatcher <Phalcon_Dispatcher>`

*implements* :doc:`Phalcon\\DispatcherInterface <Phalcon_DispatcherInterface>`, :doc:`Phalcon\\Di\\InjectionAwareInterface <Phalcon_Di_InjectionAwareInterface>`, :doc:`Phalcon\\Events\\EventsAwareInterface <Phalcon_Events_EventsAwareInterface>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/cli/dispatcher.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Dispatching is the process of taking the command-line arguments, extracting the module name, task name, action name, and optional parameters contained in it, and then instantiating a task and calling an action on it.  

.. code-block:: php

    <?php

    $di = new Phalcon\Di();
    
    $dispatcher = new Phalcon\Cli\Dispatcher();
    
      $dispatcher->setDI($di);
    
    $dispatcher->setTaskName('posts');
    $dispatcher->setActionName('index');
    $dispatcher->setParams(array());
    
    $handle = $dispatcher->dispatch();



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

public  **setTaskSuffix** (*string* $taskSuffix)

Sets the default task suffix



public  **setDefaultTask** (*string* $taskName)

Sets the default task name



public  **setTaskName** (*string* $taskName)

Sets the task name to be dispatched



public *string*  **getTaskName** ()

Gets last dispatched task name



protected  **_throwDispatchException** ()

Throws an internal exception



protected  **_handleException** ()

Handles a user exception



public *string*  **getTaskClass** ()

Possible task class name that will be located to dispatch the request



public :doc:`Phalcon\\Cli\\Task <Phalcon_Cli_Task>`  **getLastTask** ()

Returns the lastest dispatched controller



public :doc:`Phalcon\\Cli\\Task <Phalcon_Cli_Task>`  **getActiveTask** ()

Returns the active task in the dispatcher



public  **__construct** () inherited from Phalcon\\Dispatcher

Phalcon\\Dispatcher constructor



public  **setActionSuffix** (*string* $actionSuffix) inherited from Phalcon\\Dispatcher

Sets the default action suffix



public  **setDefaultModule** (*string* $module) inherited from Phalcon\\Dispatcher

Sets the default module



public *string*  **getDefaultModule** () inherited from Phalcon\\Dispatcher

Returns the default module



public  **setDefaultNamespace** (*string* $namespace) inherited from Phalcon\\Dispatcher

Sets the default namespace



public *string*  **getDefaultNamespace** () inherited from Phalcon\\Dispatcher

Returns the default namespace



public  **setDefaultHandler** (*unknown* $handlerName) inherited from Phalcon\\Dispatcher

Sets the default handler



public *string*  **getDefaultHandler** () inherited from Phalcon\\Dispatcher

Returns the default handler



public  **setDefaultAction** (*string* $actionName) inherited from Phalcon\\Dispatcher

Sets the default action name



public *string*  **getDefaultAction** () inherited from Phalcon\\Dispatcher

Returns the default action



public  **setModuleName** (*unknown* $module) inherited from Phalcon\\Dispatcher

Sets the module where the controller is (only informative)



public *string*  **getModuleName** () inherited from Phalcon\\Dispatcher

Gets the module where the controller class is



public  **setNamespaceName** (*unknown* $namespace) inherited from Phalcon\\Dispatcher

Sets the namespace where the controller class is



public *string*  **getNamespaceName** () inherited from Phalcon\\Dispatcher

Gets a namespace to be prepended to the current handler name



public  **setHandlerName** (*string* $handlerName) inherited from Phalcon\\Dispatcher

Sets the action name to be dispatched



public *string*  **getHandlerName** () inherited from Phalcon\\Dispatcher

Gets the lastest dispatched handler name



public  **setActionName** (*string* $actionName) inherited from Phalcon\\Dispatcher

Sets the action name to be dispatched



public *string*  **getActionName** () inherited from Phalcon\\Dispatcher

Gets the lastest dispatched action name



public  **setLogicBinding** (*boolean* $value) inherited from Phalcon\\Dispatcher

Enable/Disable logic binding during dispatch



public *boolean*  **isLogicBinding** () inherited from Phalcon\\Dispatcher

Check if logic binding



public  **setParams** (*array* $params) inherited from Phalcon\\Dispatcher

Sets action params to be dispatched



public *array*  **getParams** () inherited from Phalcon\\Dispatcher

Gets action params



public *boolean*  **hasParam** (*mixed* $param) inherited from Phalcon\\Dispatcher

Check if a param exists



public  **setParam** (*mixed* $param, *mixed* $value) inherited from Phalcon\\Dispatcher

Set a param by its name or numeric index



public *mixed*  **getParam** (*mixed* $param, [*string|array* $filters]) inherited from Phalcon\\Dispatcher

Gets a param by its name or numeric index



public :doc:`Phalcon\\Mvc\\Controller <Phalcon_Mvc_Controller>`  **getActiveHandler** () inherited from Phalcon\\Dispatcher

Returns the current handler to be/executed in the dispatcher



public *string*  **getActiveMethod** () inherited from Phalcon\\Dispatcher

Returns the current method to be/executed in the dispatcher



public *boolean*  **isFinished** () inherited from Phalcon\\Dispatcher

Checks if the dispatch loop is finished or has more pendent controllers/tasks to disptach



public  **setFinished** (*boolean* $finished) inherited from Phalcon\\Dispatcher

Sets the finished



public  **setReturnedValue** (*mixed* $value) inherited from Phalcon\\Dispatcher

Sets the latest returned value by an action manually



public *mixed*  **getReturnedValue** () inherited from Phalcon\\Dispatcher

Returns value returned by the lastest dispatched action



public *object*  **dispatch** () inherited from Phalcon\\Dispatcher

Dispatches a handle action taking into account the routing parameters



public *bool*  **forward** (*string|array* $forward) inherited from Phalcon\\Dispatcher

Forwards the execution flow to another controller/action Dispatchers are unique per module. Forwarding between modules is not allowed 

.. code-block:: php

    <?php

      $this->dispatcher->forward(array('controller' => 'posts', 'action' => 'index'));




public *boolean*  **wasForwarded** () inherited from Phalcon\\Dispatcher

Check if the current executed action was forwarded by another one



public *string*  **getHandlerClass** () inherited from Phalcon\\Dispatcher

Possible class name that will be located to dispatch the request



public  **camelizeNamespace** (*bool* $camelize) inherited from Phalcon\\Dispatcher

Enables/Disables automatically camelize namespace 

.. code-block:: php

    <?php

      $this->dispatcher->camelizeNamespace(FALSE);




public  **camelizeController** (*bool* $camelize) inherited from Phalcon\\Dispatcher

Enables/Disables automatically camelize controller 

.. code-block:: php

    <?php

      $this->dispatcher->camelizeController(FALSE);




public :doc:`Phalcon\\DispatcherInterface <Phalcon_DispatcherInterface>`  **setErrorHandler** (*unknown* $callback, [*int* $exception_code]) inherited from Phalcon\\Dispatcher

Set error handler



public *mixed*  **getErrorHandler** (*int* $exception_code) inherited from Phalcon\\Dispatcher

Get error handler



public *boolean*  **fireEvent** (*string* $eventName, [*string* $data], [*string* $cancelable]) inherited from Phalcon\\Dispatcher

Fires an event, implicitly calls behaviors and listeners in the events manager are notified



public *\Exception*  **getLastException** () inherited from Phalcon\\Dispatcher

Returns the last exception



public *Object*  **getLastHandler** () inherited from Phalcon\\Dispatcher

Returns the last handler



public *string*  **getPreviousNamespaceName** () inherited from Phalcon\\Dispatcher

Returns the previons namespace



public *string*  **getPreviousActionName** () inherited from Phalcon\\Dispatcher

Returns the previons action



public *array*  **getPreviousParams** () inherited from Phalcon\\Dispatcher

Returns the previons action params



public *mixed*  **getPreviousParam** (*mixed* $param, [*string|array* $filters]) inherited from Phalcon\\Dispatcher

Gets a previons param by its name or numeric index



public  **setDI** (:doc:`Phalcon\\DiInterface <Phalcon_DiInterface>` $dependencyInjector) inherited from Phalcon\\Di\\Injectable

Sets the dependency injector



public :doc:`Phalcon\\DiInterface <Phalcon_DiInterface>`  **getDI** ([*unknown* $error], [*unknown* $notUseDefault]) inherited from Phalcon\\Di\\Injectable

Returns the internal dependency injector



public  **setEventsManager** (:doc:`Phalcon\\Events\\ManagerInterface <Phalcon_Events_ManagerInterface>` $eventsManager) inherited from Phalcon\\Di\\Injectable

Sets the event manager



public :doc:`Phalcon\\Events\\ManagerInterface <Phalcon_Events_ManagerInterface>`  **getEventsManager** () inherited from Phalcon\\Di\\Injectable

Returns the internal event manager



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


