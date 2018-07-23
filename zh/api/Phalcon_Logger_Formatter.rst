Abstract class **Phalcon\\Logger\\Formatter**
=============================================

*implements* :doc:`Phalcon\\Logger\\FormatterInterface <Phalcon_Logger_FormatterInterface>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/logger/formatter.c" class="btn btn-default btn-sm">Source on GitHub</a>`

This is a base class for logger formatters


Methods
-------

public :doc:`Phalcon\\Logger\\Formatter <Phalcon_Logger_Formatter>`  **setTypeStrings** (*array* $types)

Sets the string meaning of a logger constant



public *array*  **getTypeStrings** ()

Returns the type strings



public :doc:`Phalcon\\Logger\\Formatter <Phalcon_Logger_Formatter>`  **setTypeString** (*string* $type, *string* $name)

Sets the type strings



public *string*  **getTypeString** (*integer* $type)

Returns the string meaning of a logger constant



protected  **interpolate** (*string* $message, *array* $context)

Interpolates context values into the message placeholders



abstract public  **format** (*string* $message, *int* $type, *int* $timestamp, *array* $context) inherited from Phalcon\\Logger\\FormatterInterface

Applies a format to a message before sent it to the internal log



