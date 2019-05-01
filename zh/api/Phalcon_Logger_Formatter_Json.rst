Class **Phalcon\\Logger\\Formatter\\Json**
==========================================

*extends* abstract class :doc:`Phalcon\\Logger\\Formatter <Phalcon_Logger_Formatter>`

*implements* :doc:`Phalcon\\Logger\\FormatterInterface <Phalcon_Logger_FormatterInterface>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/logger/formatter/json.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Formats messages using JSON encoding


Methods
-------

public  **__construct** ([*int* $options])

Phalcon\\Logger\\Formatter\\Json constructor



public *string*  **format** (*string* $message, *int* $type, *int* $timestamp, *array* $context)

Applies a format to a message before sent it to the internal log



public :doc:`Phalcon\\Logger\\Formatter <Phalcon_Logger_Formatter>`  **setTypeStrings** (*array* $types) inherited from Phalcon\\Logger\\Formatter

Sets the string meaning of a logger constant



public *array*  **getTypeStrings** () inherited from Phalcon\\Logger\\Formatter

Returns the type strings



public :doc:`Phalcon\\Logger\\Formatter <Phalcon_Logger_Formatter>`  **setTypeString** (*string* $type, *string* $name) inherited from Phalcon\\Logger\\Formatter

Sets the type strings



public *string*  **getTypeString** (*integer* $type) inherited from Phalcon\\Logger\\Formatter

Returns the string meaning of a logger constant



protected  **interpolate** (*string* $message, *array* $context) inherited from Phalcon\\Logger\\Formatter

Interpolates context values into the message placeholders



