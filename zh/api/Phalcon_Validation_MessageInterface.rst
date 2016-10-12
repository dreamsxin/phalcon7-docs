Interface **Phalcon\\Validation\\MessageInterface**
===================================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/validation/messageinterface.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Phalcon\\Validation\\MessageInterface initializer


Methods
-------

abstract public :doc:`Phalcon\\Validation\\MessageInterface <Phalcon_Validation_MessageInterface>`  **setType** (*string* $type)

Sets message type



abstract public *string*  **getType** ()

Returns message type



abstract public :doc:`Phalcon\\Validation\\MessageInterface <Phalcon_Validation_MessageInterface>`  **setCode** (*string* $code)

Sets message code



abstract public *string*  **getCode** ()

Returns message code



abstract public :doc:`Phalcon\\Validation\\MessageInterface <Phalcon_Validation_MessageInterface>`  **setMessage** (*string* $message)

Sets verbose message



abstract public *string*  **getMessage** ()

Returns verbose message



abstract public :doc:`Phalcon\\Validation\\MessageInterface <Phalcon_Validation_MessageInterface>`  **setField** (*string* $field)

Sets field name related to message



abstract public *string*  **getField** ()

Returns field name related to message



abstract public *string*  **__toString** ()

Magic __toString method returns verbose message



