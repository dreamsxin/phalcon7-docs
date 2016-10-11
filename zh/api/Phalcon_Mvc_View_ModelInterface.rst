Interface **Phalcon\\Mvc\\View\\ModelInterface**
================================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/phalcon/mvc/view/modelinterface.zep" class="btn btn-default btn-sm">Source on GitHub</a>`

Phalcon\\Mvc\\View\\ModelInterface initializer


Methods
-------

abstract public :doc:`Phalcon\\Mvc\\View\\ModelInterface <Phalcon_Mvc_View_ModelInterface>`  **setTemplate** (*string* $template)

Set the template to be used by this model



abstract public *string*  **getTemplate** ()

Get the template to be used by this model



abstract public :doc:`Phalcon\\Mvc\\View\\ModelInterface <Phalcon_Mvc_View_ModelInterface>`  **setVars** (*array* $params, [*boolean* $merge])

Set all the render params



abstract public  **getVars** ()

...


abstract public :doc:`Phalcon\\Mvc\\View\\ModelInterface <Phalcon_Mvc_View_ModelInterface>`  **setVar** (*string* $key, *mixed* $value)

Set a single view parameter



abstract public  **getVar** (*unknown* $key, [*unknown* $default_value])

...


abstract public :doc:`Phalcon\\Mvc\\View\\ModelInterface <Phalcon_Mvc_View_ModelInterface>`  **addChild** (*unknown* $viewmodel, [*unknown* $name], [*unknown* $append])

Add a child model



abstract public :doc:`Phalcon\\Mvc\\View\\ModelInterface <Phalcon_Mvc_View_ModelInterface>`  **appendChild** (*unknown* $viewmodel, [*unknown* $name])

Add a child model



abstract public *array*  **getChild** (*unknown* $name)

Return a child model or all child model



abstract public *boolean*  **hasChild** ()

Does the model have any children?



abstract public :doc:`Phalcon\\Mvc\\View\\ModelInterface <Phalcon_Mvc_View_ModelInterface>`  **setCaptureTo** (*string* $capture)

Set the name of the variable to capture this model to, if it is a child model



abstract public *string*  **getCaptureTo** ()

Get the name of the variable to which to capture this model



abstract public :doc:`Phalcon\\Mvc\\View\\ModelInterface <Phalcon_Mvc_View_ModelInterface>`  **setTerminal** (*boolean* $terminate)

Set flag indicating whether or not this is considered a terminal or standalone model



abstract public *boolean*  **getTerminal** ()

Is this considered a terminal or standalone model?



abstract public :doc:`Phalcon\\Mvc\\View\\ModelInterface <Phalcon_Mvc_View_ModelInterface>`  **setAppend** (*unknown* $append)

Set the view



abstract public *boolean*  **isAppend** ()

Is this append to child  with the same capture?



abstract public  **setView** (*unknown* $view)

...


abstract public :doc:`Phalcon\\Mvc\\ViewInterface <Phalcon_Mvc_ViewInterface>`  **getView** ()

Get the view



abstract public *string*  **render** ()

Renders the view



