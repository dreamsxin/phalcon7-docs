Interface **Phalcon\\Validation\\ValidatorInterface**
=====================================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/validation/validatorinterface.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Phalcon\\Validation\\ValidatorInterface initializer


Methods
-------

abstract public *mixed*  **isSetOption** (*string* $key)

Checks if an option is defined



abstract public *mixed*  **getOption** (*string* $key)

Returns an option in the validator's options Returns null if the option hasn't been set



abstract public  **setOption** (*string* $key, *mixed* $value)

Sets the validator's option



abstract public *boolean*  **validate** (:doc:`Phalcon\\ValidationInterface <Phalcon_ValidationInterface>` $validator, *string|array* $attribute, [*unknown* $allowEmpty])

Executes the validation



abstract public *boolean*  **valid** ()

Executes the validation



