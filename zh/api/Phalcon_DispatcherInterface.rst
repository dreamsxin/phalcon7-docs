Interface **Phalcon\\DispatcherInterface**
==========================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/phalcon/dispatcherinterface.zep" class="btn btn-default btn-sm">Source on GitHub</a>`

Phalcon\\DispatcherInterface initializer


Methods
-------

abstract public  **setActionSuffix** (*string* $actionSuffix)

Sets the default action suffix



abstract public  **setDefaultNamespace** (*string* $namespace)

Sets the default namespace



abstract public  **setDefaultAction** (*string* $actionName)

Sets the default action name



abstract public  **setActionName** (*string* $actionName)

Sets the action name to be dispatched



abstract public *string*  **getActionName** ()

Gets last dispatched action name



abstract public  **setParams** (*array* $params)

Sets action params to be dispatched



abstract public *array*  **getParams** ()

Gets action params



abstract public  **setParam** (*mixed* $param, *mixed* $value)

Set a param by its name or numeric index



abstract public *mixed*  **getParam** (*mixed* $param, [*string|array* $filters])

Gets a param by its name or numeric index



abstract public *boolean*  **isFinished** ()

Checks if the dispatch loop is finished or has more pendent controllers/tasks to disptach



abstract public *mixed*  **getReturnedValue** ()

Returns value returned by the lastest dispatched action



abstract public *object*  **dispatch** ()

Dispatches a handle action taking into account the routing parameters



abstract public  **forward** (*array* $forward)

Forwards the execution flow to another controller/action



abstract public  **camelizeNamespace** (*unknown* $camelize)

Forwards the execution flow to another controller/action



abstract public :doc:`Phalcon\\DispatcherInterface <Phalcon_DispatcherInterface>`  **setErrorHandler** (*unknown* $callback, [*int* $exception_code])

Set error handler



abstract public *mixed*  **getErrorHandler** (*int* $exception_code)

Get error handler



