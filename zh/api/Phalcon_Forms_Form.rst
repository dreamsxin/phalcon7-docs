Class **Phalcon\\Forms\\Form**
==============================

*extends* abstract class :doc:`Phalcon\\Di\\Injectable <Phalcon_Di_Injectable>`

*implements* :doc:`Phalcon\\Events\\EventsAwareInterface <Phalcon_Events_EventsAwareInterface>`, :doc:`Phalcon\\Di\\InjectionAwareInterface <Phalcon_Di_InjectionAwareInterface>`, Countable, Iterator, Traversable

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/forms/form.c" class="btn btn-default btn-sm">Source on GitHub</a>`

This component allows to build forms using an object-oriented interface


Constants
---------

*integer* **VALUES_RAW**

*integer* **VALUES_AS_ARRAY**

Methods
-------

public  **__construct** ([*object* $entity], [*array* $userOptions])

Phalcon\\Forms\\Form constructor



public :doc:`Phalcon\\Forms\\Form <Phalcon_Forms_Form>`  **setAction** (*string* $action)

Sets the form's action



public *string*  **getAction** ()

Returns the form's action



public :doc:`Phalcon\\Forms\\Form <Phalcon_Forms_Form>`  **setMethod** (*unknown* $method)

Sets the form's method



public *string*  **getMethod** ()

Returns the form's method



public :doc:`Phalcon\\Forms\\Form <Phalcon_Forms_Form>`  **setEnctype** (*unknown* $enctype)

Sets the form's enctype



public *string*  **getEnctype** ()

Returns the form's enctype



public :doc:`Phalcon\\Forms\\Form <Phalcon_Forms_Form>`  **setOption** (*string* $option, *mixed* $value)

Sets an option for the form



public *mixed*  **getOption** (*string* $option, [*mixed* $defaultValue])

Returns the value of an option if present



public :doc:`Phalcon\\Forms\\ElementInterface <Phalcon_Forms_ElementInterface>`  **setOptions** (*array* $options)

Sets options for the element



public *array*  **getOptions** ()

Returns the options for the element



public :doc:`Phalcon\\Forms\\Form <Phalcon_Forms_Form>`  **setEntity** (*object* $entity)

Sets the entity related to the model



public *object*  **getEntity** ()

Returns the entity related to the model



public :doc:`Phalcon\\Forms\\ElementInterface <Phalcon_Forms_ElementInterface>` [] **getElements** ()

Returns the form elements added to the form



public :doc:`Phalcon\\Forms\\Form <Phalcon_Forms_Form>`  **bind** (*array* $data, [*object* $entity], [*array* $whitelist])

Binds data to the entity



public *boolean*  **isValid** ([*array* $data], [*object* $entity])

Validates the form



public :doc:`Phalcon\\Validation\\Message\\Group <Phalcon_Validation_Message_Group>`  **getMessages** ([*boolean* $byItemName])

Returns the messages generated in the validation



public :doc:`Phalcon\\Validation\\Message\\Group <Phalcon_Validation_Message_Group>` [] **getMessagesFor** (*unknown* $name)

Returns the messages generated for a specific element



public *boolean*  **hasMessagesFor** (*unknown* $name)

Check if messages were generated for a specific element



public :doc:`Phalcon\\Forms\\Form <Phalcon_Forms_Form>`  **add** (:doc:`Phalcon\\Forms\\ElementInterface <Phalcon_Forms_ElementInterface>` $element, [*string* $postion], [*unknown* $type])

Adds an element to the form



public *string*  **render** ([*string* $name], [*array* $attributes])

Renders a specific item in the form



public :doc:`Phalcon\\Forms\\ElementInterface <Phalcon_Forms_ElementInterface>`  **get** (*string* $name)

Returns an element added to the form by its name



public *string*  **label** (*string* $name, [*unknown* $attributes])

Generate the label of a element added to the form including HTML



public *string*  **getLabel** (*string* $name)

Returns a label for an element



public *mixed*  **getValue** (*string* $name, [*unknown* $flag])

Gets a value from the internal related entity or from the default value



public *mixed*  **getValues** ([*string* $name], [*unknown* $flag])

Gets a values



public *boolean*  **has** (*string* $name)

Check if the form contains an element



public *boolean*  **remove** (*string* $name)

Removes an element from the form



public :doc:`Phalcon\\Forms\\Form <Phalcon_Forms_Form>`  **clear** ([*array* $fields])

Clears every element in the form to its default value



public *int*  **count** ()

Returns the number of elements in the form



public  **rewind** ()

Rewinds the internal iterator



public :doc:`Phalcon\\Forms\\ElementInterface <Phalcon_Forms_ElementInterface>`  **current** ()

Returns the current element in the iterator



public *int*  **key** ()

Returns the current position/key in the iterator



public  **next** ()

Moves the internal iteration pointer to the next position



public *boolean*  **valid** ()

Check if the current element in the iterator is valid



public :doc:`Phalcon\\Forms\\Form <Phalcon_Forms_Form>`  **appendMessage** (*string* $field, :doc:`Phalcon\\Validation\\Message <Phalcon_Validation_Message>` $message)

Appends a message to the form 

.. code-block:: php

    <?php

     $form->appendMessage('email', new Phalcon\Validation\Message('Must be not empty '));




public :doc:`Phalcon\\Forms\\Form <Phalcon_Forms_Form>`  **appendMessages** (*string* $field, *Phalcon\\Validation\\MessageInterface[]* $messages)

Appends a messages to the form 

.. code-block:: php

    <?php

     $form->appendMessages('email', array(new Phalcon\Validation\Message('Must be not empty '), new Phalcon\Validation\Message('Must be an email address')));




public *array*  **toArray** ()

Returns a form elements as an array



public *string*  **__toString** ()

Renders the form html



public  **setDI** (:doc:`Phalcon\\DiInterface <Phalcon_DiInterface>` $dependencyInjector) inherited from Phalcon\\Di\\Injectable

Sets the dependency injector



public :doc:`Phalcon\\DiInterface <Phalcon_DiInterface>`  **getDI** ([*unknown* $error], [*unknown* $notUseDefault]) inherited from Phalcon\\Di\\Injectable

Returns the internal dependency injector



public  **setEventsManager** (:doc:`Phalcon\\Events\\ManagerInterface <Phalcon_Events_ManagerInterface>` $eventsManager) inherited from Phalcon\\Di\\Injectable

Sets the event manager



public :doc:`Phalcon\\Events\\ManagerInterface <Phalcon_Events_ManagerInterface>`  **getEventsManager** () inherited from Phalcon\\Di\\Injectable

Returns the internal event manager



public *boolean*  **fireEvent** (*string* $eventName, [*unknown* $data], [*unknown* $cancelable]) inherited from Phalcon\\Di\\Injectable

Fires an event, implicitly calls behaviors and listeners in the events manager are notified



public *boolean*  **fireEventCancel** (*string* $eventName, [*unknown* $data], [*unknown* $cancelable]) inherited from Phalcon\\Di\\Injectable

Fires an event, implicitly calls behaviors and listeners in the events manager are notified This method stops if one of the callbacks/listeners returns boolean false



public *mixed*  **fireEventData** (*string* $eventName, [*mixed* $data]) inherited from Phalcon\\Di\\Injectable

Fires an event, return data



public *boolean*  **hasService** (*string* $name) inherited from Phalcon\\Di\\Injectable

Check whether the DI contains a service by a name



public :doc:`Phalcon\\Di\\ServiceInterface <Phalcon_Di_ServiceInterface>`  **setService** (*unknown* $name) inherited from Phalcon\\Di\\Injectable

Sets a service from the DI



public *object|null*  **getService** (*unknown* $name) inherited from Phalcon\\Di\\Injectable

Obtains a service from the DI



public *mixed*  **getResolveService** (*string* $name, [*unknown* $args], [*unknown* $noerror], [*unknown* $noshared]) inherited from Phalcon\\Di\\Injectable

Resolves the service based on its configuration



public  **attachEvent** (*string* $eventType, *Closure* $callback) inherited from Phalcon\\Di\\Injectable

Attach a listener to the events



public  **__get** (*unknown* $property) inherited from Phalcon\\Di\\Injectable

Magic method __get



public  **__sleep** () inherited from Phalcon\\Di\\Injectable

...


public  **__debugInfo** () inherited from Phalcon\\Di\\Injectable

...


