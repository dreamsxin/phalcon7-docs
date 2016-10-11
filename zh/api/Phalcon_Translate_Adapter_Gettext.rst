Class **Phalcon\\Translate\\Adapter\\Gettext**
==============================================

*extends* abstract class :doc:`Phalcon\\Translate\\Adapter <Phalcon_Translate_Adapter>`

*implements* :doc:`Phalcon\\Translate\\AdapterInterface <Phalcon_Translate_AdapterInterface>`, ArrayAccess

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/phalcon/translate/adapter/gettext.zep" class="btn btn-default btn-sm">Source on GitHub</a>`

Allows to define translation lists using PHP arrays


Methods
-------

public  **__construct** (*array* $options)

Phalcon\\Translate\\Adapter\\Gettext constructor



public *string*  **query** (*string* $index, [*array* $placeholders])

Returns the translation related to the given key



public *bool*  **exists** (*string* $index)

Check whether is defined a translation key in the internal array



public *string*  **t** (*string* $translateKey, [*array* $placeholders]) inherited from Phalcon\\Translate\\Adapter

Returns the translation string of the given key



public  **offsetSet** (*unknown* $property, *string* $value) inherited from Phalcon\\Translate\\Adapter

Sets a translation value



public *boolean*  **offsetExists** (*unknown* $property) inherited from Phalcon\\Translate\\Adapter

Check whether a translation key exists



public  **offsetUnset** (*unknown* $property) inherited from Phalcon\\Translate\\Adapter

Unsets a translation from the dictionary



public *string*  **offsetGet** (*unknown* $property) inherited from Phalcon\\Translate\\Adapter

Returns the translation related to the given key



public  **_** (*unknown* $translateKey, [*unknown* $placeholders]) inherited from Phalcon\\Translate\\Adapter

...


