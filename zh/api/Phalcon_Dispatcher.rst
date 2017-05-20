Abstract class **Phalcon\\Dispatcher**
======================================

*extends* abstract class :doc:`Phalcon\\Di\\Injectable <Phalcon_Di_Injectable>`

*implements* :doc:`Phalcon\\Events\\EventsAwareInterface <Phalcon_Events_EventsAwareInterface>`, :doc:`Phalcon\\Di\\InjectionAwareInterface <Phalcon_Di_InjectionAwareInterface>`, :doc:`Phalcon\\DispatcherInterface <Phalcon_DispatcherInterface>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/dispatcher.c" class="btn btn-default btn-sm">Source on GitHub</a>`

This is the base class for Phalcon\\Mvc\\Dispatcher and Phalcon\\Cli\\Dispatcher. This class can't be instantiated directly, you can use it to create your own dispatchers


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



public  **setDefaultModule** (*string* $module)

Sets the default module



public *string*  **getDefaultModule** ()

Returns the default module



public  **setDefaultNamespace** (*string* $namespace)

Sets the default namespace



public *string*  **getDefaultNamespace** ()

Returns the default namespace



public  **setDefaultHandler** (*unknown* $handlerName)

Sets the default handler



public *string*  **getDefaultHandler** ()

Returns the default handler



public  **setDefaultAction** (*string* $actionName)

Sets the default action name



public *string*  **getDefaultAction** ()

Returns the default action



public  **setModuleName** (*unknown* $module)

Sets the module where the controller is (only informative)



public *string*  **getModuleName** ()

Gets the module where the controller class is



public  **setNamespaceName** (*unknown* $namespace)

Sets the namespace where the controller class is



public *string*  **getNamespaceName** ()

Gets a namespace to be prepended to the current handler name



public  **setHandlerName** (*string* $handlerName)

Sets the action name to be dispatched



public *string*  **getHandlerName** ()

Gets the lastest dispatched handler name



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



public *boolean*  **hasParam** (*mixed* $param)

Check if a param exists



public  **setParam** (*mixed* $param, *mixed* $value)

Set a param by its name or numeric index



public *mixed*  **getParam** (*mixed* $param, [*string|array* $filters])

Gets a param by its name or numeric index



public :doc:`Phalcon\\Mvc\\Controller <Phalcon_Mvc_Controller>`  **getActiveHandler** ()

Returns the current handler to be/executed in the dispatcher



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



public *\Exception*  **getLastException** ()

Returns the last exception



public *Object*  **getLastHandler** ()

Returns the last handler



public *string*  **getPreviousNamespaceName** ()

Returns the previons namespace



public *string*  **getPreviousActionName** ()

Returns the previons action



public *array*  **getPreviousParams** ()

Returns the previons action params



public *mixed*  **getPreviousParam** (*mixed* $param, [*string|array* $filters])

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


