Class **Phalcon\\Mvc\\Url**
===========================

*extends* abstract class :doc:`Phalcon\\Di\\Injectable <Phalcon_Di_Injectable>`

*implements* :doc:`Phalcon\\Events\\EventsAwareInterface <Phalcon_Events_EventsAwareInterface>`, :doc:`Phalcon\\Di\\InjectionAwareInterface <Phalcon_Di_InjectionAwareInterface>`, :doc:`Phalcon\\Mvc\\UrlInterface <Phalcon_Mvc_UrlInterface>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/mvc/url.c" class="btn btn-default btn-sm">Source on GitHub</a>`

This components aids in the generation of: URIs, URLs and Paths  

.. code-block:: php

    <?php

     //Generate a URL appending the URI to the base URI
     echo $url->get('products/edit/1');
    
     //Generate a URL for a predefined route
     echo $url->get(array('for' => 'blog-post', 'title' => 'some-cool-stuff', 'year' => '2012'));



Methods
-------

public :doc:`Phalcon\\Mvc\\Url <Phalcon_Mvc_Url>`  **setBaseUri** (*string* $baseUri)

Sets a prefix for all the URIs to be generated 

.. code-block:: php

    <?php

    $url->setBaseUri('/invo/');
    $url->setBaseUri('/invo/index.php/');




public :doc:`Phalcon\\Mvc\\Url <Phalcon_Mvc_Url>`  **setStaticBaseUri** (*string* $staticBaseUri)

Sets a prefix for all static URLs generated 

.. code-block:: php

    <?php

    $url->setStaticBaseUri('/invo/');




public *string*  **getBaseUri** ()

Returns the prefix for all the generated urls. By default /



public *string*  **getStaticBaseUri** ()

Returns the prefix for all the generated static urls. By default /



public :doc:`Phalcon\\Mvc\\Url <Phalcon_Mvc_Url>`  **setBasePath** (*string* $basePath)

Sets a base path for all the generated paths 

.. code-block:: php

    <?php

    $url->setBasePath('/var/www/htdocs/');




public *string*  **getBasePath** ()

Returns the base path



public *string*  **get** ([*string|array* $uri], [*unknown* $args], [*bool|null* $local])

Generates a URL 

.. code-block:: php

    <?php

     //Generate a URL appending the URI to the base URI
     echo $url->get('products/edit/1');
    
     //Generate a URL for a predefined route
     echo $url->get(array('for' => 'blog-post', 'title' => 'some-cool-stuff', 'year' => '2012'));
     echo $url->get(array('for' => 'blog-post', 'hostname' => true, 'title' => 'some-cool-stuff', 'year' => '2012'));




public *string*  **getStatic** ([*string|array* $uri])

Generates a URL for a static resource



public *string*  **path** ([*string* $path])

Generates a local path



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


