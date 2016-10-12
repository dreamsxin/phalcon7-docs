Abstract class **Phalcon\\Translate\\Adapter**
==============================================

*implements* ArrayAccess, :doc:`Phalcon\\Translate\\AdapterInterface <Phalcon_Translate_AdapterInterface>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/translate/adapter.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Base class for Phalcon\\Translate adapters


Methods
-------

public *string*  **t** (*string* $translateKey, [*array* $placeholders])

Returns the translation string of the given key



public  **offsetSet** (*unknown* $property, *string* $value)

Sets a translation value



public *boolean*  **offsetExists** (*unknown* $property)

Check whether a translation key exists



public  **offsetUnset** (*unknown* $property)

Unsets a translation from the dictionary



public *string*  **offsetGet** (*unknown* $property)

Returns the translation related to the given key



public  **_** (*unknown* $translateKey, [*unknown* $placeholders])

...


abstract public *string*  **query** (*string* $index, [*array* $placeholders]) inherited from Phalcon\\Translate\\AdapterInterface

Returns the translation related to the given key



abstract public *bool*  **exists** (*string* $index) inherited from Phalcon\\Translate\\AdapterInterface

Check whether is defined a translation key in the internal array



