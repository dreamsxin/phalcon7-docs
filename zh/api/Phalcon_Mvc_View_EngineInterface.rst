Interface **Phalcon\\Mvc\\View\\EngineInterface**
=================================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/mvc/view/engineinterface.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Phalcon\\Mvc\\View\\EngineInterface initializer


Methods
-------

abstract public *array*  **getContent** ()

Returns cached ouput on another view stage



abstract public *string*  **partial** (*string* $partialPath)

Renders a partial inside another view



abstract public  **render** (*string* $path, *array* $params, [*boolean* $mustClean])

Renders a view using the template engine



abstract public :doc:`Phalcon\\Mvc\\View\\EngineInterface <Phalcon_Mvc_View_EngineInterface>`  **addMethod** (*string* $name, *callable* $handler)

Adds a user-defined method



abstract public *mixed*  **__call** (*string* $method, [*array* $arguments])

Handles method calls when a method is not implemented



