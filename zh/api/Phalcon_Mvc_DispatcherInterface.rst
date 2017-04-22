Interface **Phalcon\\Mvc\\DispatcherInterface**
===============================================

*extends* Phalcon\DispatcherInterface

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/mvc/dispatcherinterface.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Phalcon\\Mvc\\DispatcherInterface initializer


Methods
-------

abstract public  **setControllerSuffix** (*string* $controllerSuffix)

Sets the default controller suffix



abstract public  **setDefaultController** (*string* $controllerName)

Sets the default controller name



abstract public  **setControllerName** (*string* $controllerName, [*unknown* $isExact])

Sets the controller name to be dispatched



abstract public *string*  **getControllerName** ()

Gets last dispatched controller name



abstract public :doc:`Phalcon\\Mvc\\ControllerInterface <Phalcon_Mvc_ControllerInterface>`  **getLastController** ()

Returns the lastest dispatched controller



abstract public :doc:`Phalcon\\Mvc\\ControllerInterface <Phalcon_Mvc_ControllerInterface>`  **getActiveController** ()

Returns the active controller in the dispatcher



abstract public  **setActionSuffix** (*string* $actionSuffix) inherited from Phalcon\\DispatcherInterface

Sets the default action suffix



abstract public  **setDefaultModule** (*string* $module) inherited from Phalcon\\DispatcherInterface

Sets the default module



abstract public *string*  **getDefaultModule** () inherited from Phalcon\\DispatcherInterface

Gets the default module



abstract public  **setDefaultNamespace** (*string* $namespace) inherited from Phalcon\\DispatcherInterface

Sets the default namespace



abstract public *string*  **getDefaultNamespace** () inherited from Phalcon\\DispatcherInterface

Gets the default namespace



abstract public  **setDefaultHandler** (*string* $handlerName) inherited from Phalcon\\DispatcherInterface

Sets the default handler name



abstract public *string*  **getDefaultHandler** () inherited from Phalcon\\DispatcherInterface

Gets the default handler name



abstract public  **setDefaultAction** (*string* $actionName) inherited from Phalcon\\DispatcherInterface

Sets the default action name



abstract public *string*  **getDefaultAction** () inherited from Phalcon\\DispatcherInterface

Gets the default action name



abstract public  **setModuleName** (*unknown* $module) inherited from Phalcon\\DispatcherInterface

Sets the module name to be dispatched



abstract public *string*  **getModuleName** () inherited from Phalcon\\DispatcherInterface

Gets last dispatched module name



abstract public  **setNamespaceName** (*unknown* $namespace) inherited from Phalcon\\DispatcherInterface

Sets the namespace to be dispatched



abstract public *string*  **getNamespaceName** () inherited from Phalcon\\DispatcherInterface

Gets last dispatched namespace



abstract public  **setHandlerName** (*string* $handlerName) inherited from Phalcon\\DispatcherInterface

Sets the handler name to be dispatched



abstract public *string*  **getHandlerName** () inherited from Phalcon\\DispatcherInterface

Gets last dispatched handler name



abstract public  **setActionName** (*string* $actionName) inherited from Phalcon\\DispatcherInterface

Sets the action name to be dispatched



abstract public *string*  **getActionName** () inherited from Phalcon\\DispatcherInterface

Gets last dispatched action name



abstract public  **setParams** (*array* $params) inherited from Phalcon\\DispatcherInterface

Sets action params to be dispatched



abstract public *array*  **getParams** () inherited from Phalcon\\DispatcherInterface

Gets action params



abstract public  **hasParam** (*unknown* $param) inherited from Phalcon\\DispatcherInterface

...


abstract public  **setParam** (*mixed* $param, *mixed* $value) inherited from Phalcon\\DispatcherInterface

Set a param by its name or numeric index



abstract public *mixed*  **getParam** (*mixed* $param, [*string|array* $filters]) inherited from Phalcon\\DispatcherInterface

Gets a param by its name or numeric index



abstract public *boolean*  **isFinished** () inherited from Phalcon\\DispatcherInterface

Checks if the dispatch loop is finished or has more pendent controllers/tasks to disptach



abstract public *mixed*  **getReturnedValue** () inherited from Phalcon\\DispatcherInterface

Returns value returned by the lastest dispatched action



abstract public *object*  **dispatch** () inherited from Phalcon\\DispatcherInterface

Dispatches a handle action taking into account the routing parameters



abstract public  **forward** (*array* $forward) inherited from Phalcon\\DispatcherInterface

Forwards the execution flow to another controller/action



abstract public  **camelizeNamespace** (*unknown* $camelize) inherited from Phalcon\\DispatcherInterface

Forwards the execution flow to another controller/action



abstract public :doc:`Phalcon\\DispatcherInterface <Phalcon_DispatcherInterface>`  **setErrorHandler** (*unknown* $callback, [*int* $exception_code]) inherited from Phalcon\\DispatcherInterface

Set error handler



abstract public *mixed*  **getErrorHandler** (*int* $exception_code) inherited from Phalcon\\DispatcherInterface

Get error handler



