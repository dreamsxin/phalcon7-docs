Class **Phalcon\\Cli\\Console**
===============================

*extends* abstract class :doc:`Phalcon\\Application <Phalcon_Application>`

*implements* :doc:`Phalcon\\Di\\InjectionAwareInterface <Phalcon_Di_InjectionAwareInterface>`, :doc:`Phalcon\\Events\\EventsAwareInterface <Phalcon_Events_EventsAwareInterface>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/cli/console.c" class="btn btn-default btn-sm">Source on GitHub</a>`

This component allows to create CLI applications using Phalcon


Methods
-------

public  **__construct** ([*unknown* $dependencyInjector])

Phalcon\\Cli\\Console constructor



public  **addModules** (*array* $modules)

Merge modules with the existing ones 

.. code-block:: php

    <?php

    $application->addModules(array(
    	'admin' => array(
    		'className' => 'Multiple\Admin\Module',
    		'path' => '../apps/admin/Module.php'
    	)
    ));




public *mixed*  **handle** ([*unknown* $data])

Handle the command-line arguments. 

.. code-block:: php

    <?php

     	$arguments = array(
     		'task' => 'taskname',
     		'action' => 'action',
     		'params' => array('parameter1', 'parameter2')
     	);
     	$console->handle($arguments);




public  **registerModules** (*array* $modules, [*boolean* $merge]) inherited from Phalcon\\Application

Register an array of modules present in the application 

.. code-block:: php

    <?php

    $this->registerModules(array(
    	'frontend' => array(
    		'className' => 'Multiple\Frontend\Module',
    		'path' => '../apps/frontend/Module.php'
    	),
    	'backend' => array(
    		'className' => 'Multiple\Backend\Module',
    		'path' => '../apps/backend/Module.php'
    	)
    ));




public *array*  **getModules** () inherited from Phalcon\\Application

Return the modules registered in the application



public :doc:`Phalcon\\Application <Phalcon_Application>`  **setDefaultModule** (*string* $defaultModule) inherited from Phalcon\\Application

Sets the module name to be used if the router doesn't return a valid module



public *string*  **getDefaultModule** () inherited from Phalcon\\Application

Returns the default module name



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


