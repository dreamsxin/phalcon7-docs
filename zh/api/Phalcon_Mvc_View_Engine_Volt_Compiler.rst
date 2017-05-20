Class **Phalcon\\Mvc\\View\\Engine\\Volt\\Compiler**
====================================================

*extends* abstract class :doc:`Phalcon\\Di\\Injectable <Phalcon_Di_Injectable>`

*implements* :doc:`Phalcon\\Events\\EventsAwareInterface <Phalcon_Events_EventsAwareInterface>`, :doc:`Phalcon\\Di\\InjectionAwareInterface <Phalcon_Di_InjectionAwareInterface>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/mvc/view/engine/volt/compiler.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Methods
-------

public  **__construct** ([:doc:`Phalcon\\Mvc\\ViewInterface <Phalcon_Mvc_ViewInterface>` $view])

...


public  **setOptions** (*array* $options)

...


public  **setOption** (*unknown* $option, *unknown* $value)

...


public  **getOption** (*unknown* $option)

...


public  **getOptions** ()

...


final public  **fireExtensionEvent** (*unknown* $name, [*unknown* $arguments])

...


public  **addExtension** (*unknown* $extension)

...


public  **getExtensions** ()

...


public  **addFunction** (*unknown* $name, *unknown* $definition)

...


public  **getFunctions** ()

...


public  **addFilter** (*unknown* $name, *unknown* $definition)

...


public  **getFilters** ()

...


public  **setUniquePrefix** (*unknown* $prefix)

...


public  **getUniquePrefix** ()

...


public  **attributeReader** (*array* $expr)

...


public  **functionCall** (*array* $expr)

...


public  **resolveTest** (*array* $test, *unknown* $left)

...


final protected  **resolveFilter** (*array* $filter, *unknown* $left)

...


final public  **expression** (*array* $expr)

...


final protected  **_statementListOrExtends** (*unknown* $statements)

...


public  **compileForeach** (*array* $statement, [*unknown* $extendsMode])

...


public  **compileForElse** ()

...


public  **compileIf** (*array* $statement, [*unknown* $extendsMode])

...


public  **compileElseIf** (*array* $statement)

...


public  **compileCache** (*array* $statement, [*unknown* $extendsMode])

...


public  **compileSet** (*array* $statement)

...


public  **compileDo** (*array* $statement)

...


public  **compileReturn** (*array* $statement)

...


public  **compileAutoEscape** (*array* $statement, *unknown* $extendsMode)

...


public  **compileEcho** (*array* $statement)

...


public  **compileInclude** (*array* $statement)

...


public  **compileMacro** (*array* $statement, *unknown* $extendsMode)

...


public  **compileCall** (*array* $statement, *unknown* $extendsMode)

...


final protected  **_statementList** (*array* $statements, [*unknown* $extendsMode])

...


protected  **_compileSource** (*unknown* $viewCode, [*unknown* $extendsMode])

...


public  **compileString** (*unknown* $viewCode, [*unknown* $extendsMode])

...


public  **compileFile** (*unknown* $path, *unknown* $compiledPath, [*unknown* $extendsMode])

...


public  **compile** (*unknown* $templatePath, [*unknown* $extendsMode])

...


public  **getTemplatePath** ()

...


public  **getCompiledTemplatePath** ()

...


public  **parse** (*unknown* $viewCode)

...


protected  **getFinalPath** (*unknown* $path)

...


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


