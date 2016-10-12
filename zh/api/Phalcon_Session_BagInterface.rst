Interface **Phalcon\\Session\\BagInterface**
============================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/session/baginterface.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Phalcon\\Session\\BagInterface initializer


Methods
-------

abstract public  **initialize** ()

Initializes the session bag. This method must not be called directly, the class calls it when its internal data is accesed



abstract public  **destroy** ()

Destroyes the session bag



abstract public  **set** (*string* $property, *string* $value)

Setter of values



abstract public *mixed*  **get** (*string* $property, [*mixed* $defaultValue])

Getter of values



abstract public *boolean*  **has** (*string* $property)

Isset property



abstract public  **remove** (*string* $property)

Unset property



