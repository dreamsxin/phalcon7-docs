Class **Phalcon\\Mvc\\View\\Model**
===================================

*implements* :doc:`Phalcon\\Mvc\\View\\ModelInterface <Phalcon_Mvc_View_ModelInterface>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/mvc/view/model.c" class="btn btn-default btn-sm">Source on GitHub</a>`

This component allows to render views without hicherquical levels  

.. code-block:: php

    <?php

     $view = new Phalcon\Mvc\View\Model();
     echo $view->render('templates/my-view', array('content' => $html));



Methods
-------

public  **__construct** ([*unknown* $vars], [*unknown* $template], [*unknown* $capture])

Phalcon\\Mvc\\View\\Model constructor



public :doc:`Phalcon\\Mvc\\View\\ModelInterface <Phalcon_Mvc_View_ModelInterface>`  **setTemplate** (*string* $template)

Set the template to be used by this model



public *string*  **getTemplate** ()

Get the template to be used by this model



public :doc:`Phalcon\\Mvc\\View\\ModelInterface <Phalcon_Mvc_View_ModelInterface>`  **setVars** (*array* $params, [*boolean* $merge])

Set all the render params



public *string*  **getVars** ()

Get the vars



public :doc:`Phalcon\\Mvc\\View\\ModelInterface <Phalcon_Mvc_View_ModelInterface>`  **setVar** (*string* $key, *mixed* $value)

Set a single view parameter



public *mixed*  **getVar** (*string* $key, [*unknown* $default_value])

Get the vars



public :doc:`Phalcon\\Mvc\\View\\ModelInterface <Phalcon_Mvc_View_ModelInterface>`  **addChild** (*unknown* $viewmodel, [*unknown* $name], [*unknown* $append])

Add a child model



public :doc:`Phalcon\\Mvc\\View\\ModelInterface <Phalcon_Mvc_View_ModelInterface>`  **appendChild** (*unknown* $viewmodel, [*unknown* $name])

Append a child model



public *array*  **getChild** (*unknown* $name)

Return a child model or all child model



public *boolean*  **hasChild** ()

Does the model have any children?



public :doc:`Phalcon\\Mvc\\View\\ModelInterface <Phalcon_Mvc_View_ModelInterface>`  **setCaptureTo** (*string* $capture)

Set the name of the variable to capture this model to, if it is a child model



public *string*  **getCaptureTo** ()

Get the name of the variable to which to capture this model



public :doc:`Phalcon\\Mvc\\View\\ModelInterface <Phalcon_Mvc_View_ModelInterface>`  **setTerminal** (*boolean* $terminate)

Set flag indicating whether or not this is considered a terminal or standalone model



public *boolean*  **getTerminal** ()

Is this considered a terminal or standalone model?



public :doc:`Phalcon\\Mvc\\View\\ModelInterface <Phalcon_Mvc_View_ModelInterface>`  **setAppend** (*boolean* $append)

Set flag indicating whether or not append to child  with the same capture



public *boolean*  **isAppend** ()

Is this append to child  with the same capture?



public :doc:`Phalcon\\Mvc\\View\\ModelInterface <Phalcon_Mvc_View_ModelInterface>`  **setView** (:doc:`Phalcon\\Mvc\\ViewInterface <Phalcon_Mvc_ViewInterface>` $view)

Set the view



public :doc:`Phalcon\\Mvc\\ViewInterface <Phalcon_Mvc_ViewInterface>`  **getView** ()

Get the view



public *string*  **render** ()

Renders the view



public  **__set** (*unknown* $property, *mixed* $value)

Magic method to pass variables to the views



public *mixed*  **__get** (*unknown* $property)

Magic method to retrieve a variable passed to the view



public *boolean*  **__isset** (*unknown* $property)

Magic method to inaccessible a variable passed to the view



public  **__toString** ()

...


