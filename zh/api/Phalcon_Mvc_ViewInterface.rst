Interface **Phalcon\\Mvc\\ViewInterface**
=========================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/mvc/viewinterface.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Phalcon\\Mvc\\ViewInterface initializer


Methods
-------

abstract public  **setViewsDir** (*string* $viewsDir)

Sets views directory. Depending of your platform, always add a trailing slash or backslash



abstract public *string*  **getViewsDir** ()

Gets views directory



abstract public  **setLayoutsDir** (*string* $layoutsDir)

Sets the layouts sub-directory. Must be a directory under the views directory. Depending of your platform, always add a trailing slash or backslash



abstract public *string*  **getLayoutsDir** ()

Gets the current layouts sub-directory



abstract public  **setPartialsDir** (*string* $partialsDir)

Sets a partials sub-directory. Must be a directory under the views directory. Depending of your platform, always add a trailing slash or backslash



abstract public *string*  **getPartialsDir** ()

Gets the current partials sub-directory



abstract public :doc:`Phalcon\\Mvc\\ViewInterface <Phalcon_Mvc_ViewInterface>`  **setBasePath** (*string* $basePath)

Sets base path. Depending of your platform, always add a trailing slash or backslash



abstract public *string*  **getBasePath** ()

Gets base path



abstract public *string*  **getCurrentRenderLevel** ()

Gets the current render level



abstract public *string*  **getRenderLevel** ()

Gets the render level for the view



abstract public :doc:`Phalcon\\Mvc\\ViewInterface <Phalcon_Mvc_ViewInterface>`  **setRenderLevel** (*string* $level)

Sets the render level for the view



abstract public  **disableLevel** (*string* $level)

Sets the render level for the view



abstract public  **getDisabledLevels** ()

...


abstract public :doc:`Phalcon\\Mvc\\ViewInterface <Phalcon_Mvc_ViewInterface>`  **setMainView** (*unknown* $viewPath)

Disables a specific level of rendering



abstract public *string*  **getMainView** ()

Returns the name of the main view



abstract public  **setLayout** (*string* $layout)

Change the layout to be used instead of using the name of the latest controller name



abstract public *string*  **getLayout** ()

Returns the name of the main view



abstract public  **setTemplateBefore** (*string|array* $templateBefore)

Appends template before controller layout



abstract public  **cleanTemplateBefore** ()

Resets any template before layouts



abstract public  **setTemplateAfter** (*string|array* $templateAfter)

Appends template after controller layout



abstract public  **cleanTemplateAfter** ()

Resets any template before layouts



abstract public  **setParamToView** (*string* $key, *mixed* $value)

Adds parameters to views (alias of setVar)



abstract public *array*  **getParamsToView** ()

Returns parameters to views



abstract public :doc:`Phalcon\\Mvc\\ViewInterface <Phalcon_Mvc_ViewInterface>`  **setVars** (*array* $params, [*boolean* $merge])

Set all the render params



abstract public :doc:`Phalcon\\Mvc\\ViewInterface <Phalcon_Mvc_ViewInterface>`  **setVar** (*string* $key, *mixed* $value)

Adds parameters to views



abstract public *mixed*  **getVar** (*string* $key)

Returns a parameter previously set in the view



abstract public :doc:`Phalcon\\Mvc\\ViewInterface <Phalcon_Mvc_ViewInterface>`  **setControllerName** (*string* $controllerName)

Sets the controller name to be view



abstract public *string*  **getControllerName** ()

Gets the name of the controller rendered



abstract public :doc:`Phalcon\\Mvc\\ViewInterface <Phalcon_Mvc_ViewInterface>`  **setActionName** (*string* $actionName)

Sets the action name to be view



abstract public *string*  **getActionName** ()

Gets the name of the action rendered



abstract public :doc:`Phalcon\\Mvc\\ViewInterface <Phalcon_Mvc_ViewInterface>`  **setParams** (*array* $params)

Sets the extra parameters to be view



abstract public *array*  **getParams** ()

Gets extra parameters of the action rendered



abstract public  **start** ()

Starts rendering process enabling the output buffering



abstract public  **registerEngines** (*array* $engines)

Register templating engines



abstract public  **getRegisteredEngines** ()

...


abstract public *array*  **getEngines** ()

Returns the registered templating engines, if none is registered it will use Phalcon\\Mvc\\View\\Engine\\Php



abstract public *boolean*  **exists** (*string* $view, [*unknown* $absolute_path])

Checks whether a view file exists



abstract public  **render** (*string* $controllerName, *string* $actionName, [*array* $params], [*unknown* $namespace], [*unknown* $viewModel])

Executes render process from dispatching data



abstract public  **pick** (*string* $renderView)

Choose a view different to render than last-controller/last-action



abstract public *string*  **partial** (*string* $partialPath)

Renders a partial view



abstract public *string*  **getRender** (*string* $controllerName, *string* $actionName, [*array* $params], [*mixed* $configCallback])

Perform the automatic rendering returning the output as a string



abstract public :doc:`Phalcon\\Mvc\\ViewInterface <Phalcon_Mvc_ViewInterface>`  **finish** ()

Finishes the render process by stopping the output buffering



abstract public *boolean*  **isCaching** ()

Check if the component is currently caching the output content



abstract public :doc:`Phalcon\\Cache\\BackendInterface <Phalcon_Cache_BackendInterface>`  **getCache** ()

Returns the cache instance used to cache



abstract public  **cache** ([*boolean|array* $options])

Cache the actual view render to certain level



abstract public  **setContent** (*string* $content, [*unknown* $append])

Externally sets the view content



abstract public *string*  **getContent** ()

Returns cached ouput from another view stage



abstract public  **startSection** (*string* $name)

Start a new section block



abstract public  **stopSection** ()

Stop the current section block



abstract public *string*  **section** (*unknown* $name, [*unknown* $defaultValue])

Returns the content for a section block



abstract public *string*  **getActiveRenderPath** ()

Returns the path of the view that is currently rendered



abstract public  **disable** ()

Disables the auto-rendering process



abstract public  **enable** ()

Enables the auto-rendering process



abstract public *boolean*  **isDisabled** ()

Whether automatic rendering is enabled



abstract public :doc:`Phalcon\\Mvc\\ViewInterface <Phalcon_Mvc_ViewInterface>`  **enableNamespaceView** ()

Enables namespace view render



abstract public :doc:`Phalcon\\Mvc\\ViewInterface <Phalcon_Mvc_ViewInterface>`  **disableNamespaceView** ()

Disables namespace view render



abstract public :doc:`Phalcon\\Mvc\\ViewInterface <Phalcon_Mvc_ViewInterface>`  **enableLowerCase** ()

Enables to lower case view path



abstract public :doc:`Phalcon\\Mvc\\ViewInterface <Phalcon_Mvc_ViewInterface>`  **disableLowerCase** ()

Disables to lower case view path



abstract public :doc:`Phalcon\\Mvc\\ViewInterface <Phalcon_Mvc_ViewInterface>`  **setConverter** (*string* $name, *callable* $converter)

Adds a converter



abstract public *callable|null*  **getConverter** (*unknown* $name)

Returns the router converter



abstract public  **reset** ()

Resets the view component to its factory default values



