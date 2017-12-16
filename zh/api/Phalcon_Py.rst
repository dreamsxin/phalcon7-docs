Class **Phalcon\\Py**
=====================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/py.c" class="btn btn-default btn-sm">Source on GitHub</a>`




Methods
-------

public static  **import** (*unknown* $name)

Importing Modules



public static  **construct** (*string* $moduleName, *string* $className)

Class constructor



public static  **callFunction** (*string* $moduleName, *string* $functionName)

Call the requested function in the requested module



public static  **callMethod** (:doc:`Phalcon\\Py\\Object <Phalcon_Py_Object>` $object, *string* $name, [*array* $args])

Calls a method of the object



public static  **eval** (*string* $expr)

Evaluate a string of code by passing it to the Python interpreter



public static  **exec** (*string* $command)

Execute a string of code by passing it to the Python interpreter



public static  **list** (*array* $val)

PHP array to Python list



public static  **tuple** (*array* $val)

PHP array to Python tuple



public static  **dict** (*array* $val)

PHP array to Python dict



public static  **val** (*mixed* $val)

PHP val to Python val



public static  **version** ()

Returns the Python interpreter's version as a string



