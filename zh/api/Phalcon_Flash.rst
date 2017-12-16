Abstract class **Phalcon\\Flash**
=================================

*extends* abstract class :doc:`Phalcon\\Di\\Injectable <Phalcon_Di_Injectable>`

*implements* :doc:`Phalcon\\Events\\EventsAwareInterface <Phalcon_Events_EventsAwareInterface>`, :doc:`Phalcon\\Di\\InjectionAwareInterface <Phalcon_Di_InjectionAwareInterface>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/flash.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Shows HTML notifications related to different circumstances. Classes can be stylized using CSS  

.. code-block:: php

    <?php

     $flash->success("The record was successfully deleted");
     $flash->error("Cannot open the file");



Methods
-------

public  **__construct** ([*array* $cssClasses])

Phalcon\\Flash constructor



public :doc:`Phalcon\\FlashInterface <Phalcon_FlashInterface>`  **setImplicitFlush** (*boolean* $implicitFlush)

Set whether the output must be implictly flushed to the output or returned as string



public :doc:`Phalcon\\FlashInterface <Phalcon_FlashInterface>`  **setAutomaticHtml** (*boolean* $automaticHtml)

Set if the output must be implictily formatted with HTML



public :doc:`Phalcon\\FlashInterface <Phalcon_FlashInterface>`  **setCssClasses** (*array* $cssClasses)

Set an array with CSS classes to format the messages



public *string*  **error** (*string* $message)

Shows a HTML error message 

.. code-block:: php

    <?php

     $flash->error('This is an error');




public *string*  **notice** (*string* $message)

Shows a HTML notice/information message 

.. code-block:: php

    <?php

     $flash->notice('This is an information');




public *string*  **success** (*string* $message)

Shows a HTML success message 

.. code-block:: php

    <?php

     $flash->success('The process was finished successfully');




public *string*  **warning** (*string* $message)

Shows a HTML warning message 

.. code-block:: php

    <?php

     $flash->warning('Hey, this is important');




public  **outputMessage** (*string* $type, *string* $message)

Outputs a message formatting it with HTML 

.. code-block:: php

    <?php

     $flash->outputMessage('error', $message);




public  **setDI** (:doc:`Phalcon\\DiInterface <Phalcon_DiInterface>` $dependencyInjector) inherited from Phalcon\\Di\\Injectable

Sets the dependency injector



public :doc:`Phalcon\\DiInterface <Phalcon_DiInterface>`  **getDI** ([*unknown* $error], [*unknown* $notUseDefault]) inherited from Phalcon\\Di\\Injectable

Returns the internal dependency injector



public  **setEventsManager** (:doc:`Phalcon\\Events\\ManagerInterface <Phalcon_Events_ManagerInterface>` $eventsManager) inherited from Phalcon\\Di\\Injectable

Sets the event manager



public :doc:`Phalcon\\Events\\ManagerInterface <Phalcon_Events_ManagerInterface>`  **getEventsManager** () inherited from Phalcon\\Di\\Injectable

Returns the internal event manager



public *boolean*  **fireEvent** (*string* $eventName, [*mixed* $data], [*unknown* $cancelable]) inherited from Phalcon\\Di\\Injectable

Fires an event, implicitly calls behaviors and listeners in the events manager are notified



public *mixed*  **fireEventCancel** (*string* $eventName, [*mixed* $data], [*unknown* $cancelable]) inherited from Phalcon\\Di\\Injectable

Fires an event, can stop the event by returning to the false



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


