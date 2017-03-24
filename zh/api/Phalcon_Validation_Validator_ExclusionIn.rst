Class **Phalcon\\Validation\\Validator\\ExclusionIn**
=====================================================

*extends* abstract class :doc:`Phalcon\\Validation\\Validator <Phalcon_Validation_Validator>`

*implements* :doc:`Phalcon\\Validation\\ValidatorInterface <Phalcon_Validation_ValidatorInterface>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/validation/validator/exclusionin.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Check if a value is not included into a list of values  

.. code-block:: php

    <?php

    use Phalcon\Validation\Validator\ExclusionIn;
    
    $validator->add('status', new ExclusionIn(array(
       'message' => 'The status must not be A or B',
       'domain' => array('A', 'B')
    )));



Methods
-------

public *boolean*  **validate** (:doc:`Phalcon\\Validation <Phalcon_Validation>` $validator, *string* $attribute, [*unknown* $allowEmpty])

Executes the validation



public *boolean*  **valid** ()

Executes the validation



public  **__construct** ([*array* $options]) inherited from Phalcon\\Validation\\Validator

Phalcon\\Validation\\Validator constructor



public *mixed*  **isSetOption** (*string* $key) inherited from Phalcon\\Validation\\Validator

Checks if an option is defined



public *mixed*  **getOption** (*string* $key) inherited from Phalcon\\Validation\\Validator

Returns an option in the validator's options Returns null if the option hasn't been set



public  **setOption** (*string* $key, *mixed* $value) inherited from Phalcon\\Validation\\Validator

Sets an option in the validator



public *mixed*  **getType** () inherited from Phalcon\\Validation\\Validator

Gets an type in the validator



