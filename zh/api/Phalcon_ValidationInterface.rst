Interface **Phalcon\\ValidationInterface**
==========================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/phalcon/validationinterface.zep" class="btn btn-default btn-sm">Source on GitHub</a>`

Phalcon\\Mvc\\Model\\ValidatorInterface initializer


Methods
-------

abstract public :doc:`Phalcon\\Validation\\Message\\Group <Phalcon_Validation_Message_Group>`  **validate** (*array|object* $data, [*object* $entity])

Validate a set of data according to a set of rules



abstract public :doc:`Phalcon\\Validation <Phalcon_Validation>`  **add** (*string* $attribute, *unknown* $validator)

Adds a validator to a field



abstract public :doc:`Phalcon\\Validation\\Message\\Group <Phalcon_Validation_Message_Group>`  **getMessages** ()

Returns the registered validators



