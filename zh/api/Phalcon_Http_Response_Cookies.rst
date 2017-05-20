Class **Phalcon\\Http\\Response\\Cookies**
==========================================

*extends* abstract class :doc:`Phalcon\\Di\\Injectable <Phalcon_Di_Injectable>`

*implements* :doc:`Phalcon\\Events\\EventsAwareInterface <Phalcon_Events_EventsAwareInterface>`, :doc:`Phalcon\\Di\\InjectionAwareInterface <Phalcon_Di_InjectionAwareInterface>`, :doc:`Phalcon\\Http\\Response\\CookiesInterface <Phalcon_Http_Response_CookiesInterface>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/http/response/cookies.c" class="btn btn-default btn-sm">Source on GitHub</a>`

This class is a bag to manage the cookies A cookies bag is automatically registered as part of the 'response' service in the DI


Methods
-------

public  **__construct** (*unknown* $name, [*unknown* $value], [*int* $expire], [*string* $path], [*boolean* $secure], [*string* $domain], [*boolean* $httpOnly])

Phalcon\\Http\\Response\\Cookie constructor



public :doc:`Phalcon\\Http\\Response\\Cookies <Phalcon_Http_Response_Cookies>`  **useEncryption** (*boolean* $useEncryption)

Set if cookies in the bag must be automatically encrypted/decrypted



public *boolean*  **isUsingEncryption** ()

Returns if the bag is automatically encrypting/decrypting cookies



public :doc:`Phalcon\\Http\\Response\\Cookies <Phalcon_Http_Response_Cookies>`  **set** (*string* $name, [*mixed* $value], [*int* $expire], [*string* $path], [*boolean* $secure], [*string* $domain], [*boolean* $httpOnly])

Sets a cookie to be sent at the end of the request This method overrides any cookie set before with the same name



public :doc:`Phalcon\\Http\\Cookie <Phalcon_Http_Cookie>`  **get** (*string* $name)

Gets a cookie from the bag



public *boolean*  **has** (*string* $name)

Check if a cookie is defined in the bag or exists in the $_COOKIE superglobal



public *boolean*  **delete** (*string* $name)

Deletes a cookie by its name This method does not removes cookies from the $_COOKIE superglobal



public *boolean*  **send** ()

Sends the cookies to the client Cookies aren't sent if headers are sent in the current request



public :doc:`Phalcon\\Http\\Response\\Cookies <Phalcon_Http_Response_Cookies>`  **reset** ()

Reset set cookies



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


