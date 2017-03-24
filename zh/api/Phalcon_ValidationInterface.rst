Interface **Phalcon\\ValidationInterface**
==========================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/validationinterface.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Phalcon\\Mvc\\Model\\ValidatorInterface initializer


Methods
-------

abstract public :doc:`Phalcon\\Validation\\Message\\Group <Phalcon_Validation_Message_Group>`  **validate** (*array|object* $data, [*object* $entity])

Validate a set of data according to a set of rules



abstract public :doc:`Phalcon\\Validation <Phalcon_Validation>`  **add** (*string* $attribute, *unknown* $validator)

Adds a validator to a field



abstract public *string*  **getLabel** (*string|array* $field)

Get label for field



abstract public *mixed*  **getValue** (*string* $attribute, [*unknown* $entity])

Gets the a value to validate in the array/object data source



abstract public  **appendMessage** (:doc:`Phalcon\\Validation\\MessageInterface <Phalcon_Validation_MessageInterface>` $message)

...


abstract public :doc:`Phalcon\\Validation\\Message\\Group <Phalcon_Validation_Message_Group>`  **getMessages** ()

Returns the registered validators



