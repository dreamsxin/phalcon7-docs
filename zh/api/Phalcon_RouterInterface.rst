Interface **Phalcon\\RouterInterface**
======================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/routerinterface.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Phalcon\\Mvc\\RouterInterface initializer


Methods
-------

abstract public  **setDefaultModule** (*string* $moduleName)

Sets the name of the default module



abstract public *string*  **getDefaultModule** ()

Gets the name of the default module



abstract public  **setDefaultNamespace** (*unknown* $namespaceName)

...


abstract public  **getDefaultNamespace** ()

...


abstract public  **setDefaultHandler** (*string* $handlerName)

Sets the default handle name



abstract public *string*  **getDefaultHandler** ()

Gets the default handle name



abstract public  **setDefaultAction** (*string* $actionName)

Sets the default action name



abstract public *string*  **getDefaultAction** ()

Gets the default action name



abstract public  **setDefaultParams** (*array* $params)

Sets the default extra params



abstract public *array*  **getDefaultParams** ()

Gets the default extra params



abstract public  **setCaseSensitive** (*boolean* $caseSensitive)

Sets the case sensitive



abstract public *int*  **getCaseSensitive** ()

Gets the case sensitive



abstract public  **setMode** (*int* $mode)

Sets the mode



abstract public *int*  **getMode** ()

Gets the mode



abstract public  **setModuleName** (*string* $moduleName)

Sets processed module name



abstract public *string*  **getModuleName** ()

Returns processed module name



abstract public  **setNamespaceName** (*string* $namespaceName)

Sets processed namespace name



abstract public *string*  **getNamespaceName** ()

Returns processed namespace name



abstract public  **setHandlerName** (*unknown* $handlerName)

Sets processed handle name



abstract public *string*  **getHandlerName** ()

Returns processed handle name



abstract public  **setActionName** (*string* $actionName)

Sets processed action name



abstract public *string*  **getActionName** ()

Returns processed action name



abstract public  **setParams** (*array* $params)

Sets processed extra params



abstract public *array*  **getParams** ()

Returns processed extra params



abstract public  **handle** ([*string* $uri])

Handles routing information received from the rewrite engine



