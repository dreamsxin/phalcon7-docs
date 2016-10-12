Class **Phalcon\\Validation**
=============================

*extends* abstract class :doc:`Phalcon\\DI\\Injectable <Phalcon_DI_Injectable>`

*implements* :doc:`Phalcon\\Events\\EventsAwareInterface <Phalcon_Events_EventsAwareInterface>`, :doc:`Phalcon\\DI\\InjectionAwareInterface <Phalcon_DI_InjectionAwareInterface>`, :doc:`Phalcon\\ValidationInterface <Phalcon_ValidationInterface>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/validation.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Allows to validate data using validators


Methods
-------

public  **__construct** ([*array* $validators])

Phalcon\\Validation constructor



public :doc:`Phalcon\\Validation\\Message\\Group <Phalcon_Validation_Message_Group>`  **validate** (*array|object* $data, [*object* $entity])

Validate a set of data according to a set of rules



public :doc:`Phalcon\\Validation <Phalcon_Validation>`  **add** (*string* $attribute, *unknown* $validator)

Adds a validator to a field



public :doc:`Phalcon\\Validation <Phalcon_Validation>`  **setFilters** (*array|string* $attribute, *unknown* $filters)

Adds filters to the field



public *mixed*  **getFilters** ([*string* $attribute])

Returns all the filters or a specific one



public *array*  **getValidators** ()

Returns the validators added to the validation



public :doc:`Phalcon\\Validation <Phalcon_Validation>`  **setEntity** ([*object* $entity])

Sets the bound entity



public *object*  **getEntity** ()

Returns the bound entity



public :doc:`Phalcon\\Validation\\Message\\Group <Phalcon_Validation_Message_Group>`  **getMessages** ()

Returns the registered validators



public :doc:`Phalcon\\Validation <Phalcon_Validation>`  **appendMessage** (:doc:`Phalcon\\Validation\\MessageInterface <Phalcon_Validation_MessageInterface>` $message)

Appends a message to the messages list



public :doc:`Phalcon\\Validation <Phalcon_Validation>`  **bind** (*object* $entity, *object|array* $data)

Assigns the data to an entity The entity is used to obtain the validation values



public *mixed*  **getValue** (*string* $attribute)

Gets the a value to validate in the array/object data source



public  **setDefaultMessages** ([*unknown* $messages])

...


public  **getDefaultMessage** (*unknown* $type)

...


public  **setLabels** (*array* $labels)

Adds labels for fields



public *mixed*  **getLabel** (*string* $field)

Get label for field



public  **setDI** (:doc:`Phalcon\\DiInterface <Phalcon_DiInterface>` $dependencyInjector) inherited from Phalcon\\DI\\Injectable

Sets the dependency injector



public :doc:`Phalcon\\DiInterface <Phalcon_DiInterface>`  **getDI** ([*unknown* $error]) inherited from Phalcon\\DI\\Injectable

Returns the internal dependency injector



public  **setEventsManager** (:doc:`Phalcon\\Events\\ManagerInterface <Phalcon_Events_ManagerInterface>` $eventsManager) inherited from Phalcon\\DI\\Injectable

Sets the event manager



public :doc:`Phalcon\\Events\\ManagerInterface <Phalcon_Events_ManagerInterface>`  **getEventsManager** () inherited from Phalcon\\DI\\Injectable

Returns the internal event manager



public *boolean*  **fireEvent** (*string* $eventName, [*unknown* $data], [*unknown* $cancelable]) inherited from Phalcon\\DI\\Injectable

Fires an event, implicitly calls behaviors and listeners in the events manager are notified



public *boolean*  **fireEventCancel** (*string* $eventName, [*unknown* $data], [*unknown* $cancelable]) inherited from Phalcon\\DI\\Injectable

Fires an event, implicitly calls behaviors and listeners in the events manager are notified This method stops if one of the callbacks/listeners returns boolean false



public *boolean*  **hasService** (*string* $name) inherited from Phalcon\\DI\\Injectable

Check whether the DI contains a service by a name



public *mixed*  **getResolveService** (*string* $name, [*unknown* $args], [*unknown* $noerror], [*unknown* $noshared]) inherited from Phalcon\\DI\\Injectable

Resolves the service based on its configuration



public  **__get** (*unknown* $property) inherited from Phalcon\\DI\\Injectable

Magic method __get



public  **__sleep** () inherited from Phalcon\\DI\\Injectable

...


public  **__debugInfo** () inherited from Phalcon\\DI\\Injectable

...


