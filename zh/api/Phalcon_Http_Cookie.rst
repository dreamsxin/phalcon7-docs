Class **Phalcon\\Http\\Cookie**
===============================

*extends* abstract class :doc:`Phalcon\\Di\\Injectable <Phalcon_Di_Injectable>`

*implements* :doc:`Phalcon\\Events\\EventsAwareInterface <Phalcon_Events_EventsAwareInterface>`, :doc:`Phalcon\\Di\\InjectionAwareInterface <Phalcon_Di_InjectionAwareInterface>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/http/cookie.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Provide OO wrappers to manage a HTTP cookie


Methods
-------

public  **__construct** (*string* $name, [*mixed* $value], [*int* $expire], [*string* $path], [*boolean* $secure], [*string* $domain], [*boolean* $httpOnly])

Phalcon\\Http\\Cookie constructor



public *Phalcon\\Http\\CookieInterface*  **setValue** (*string* $value)

Sets the cookie's value



public *mixed*  **getValue** ([*string|array* $filters], [*string* $defaultValue])

Returns the cookie's value



public :doc:`Phalcon\\Http\\Cookie <Phalcon_Http_Cookie>`  **send** ()

Sends the cookie to the HTTP client Stores the cookie definition in session



public :doc:`Phalcon\\Http\\Cookie <Phalcon_Http_Cookie>`  **restore** ()

Reads the cookie-related info from the SESSION to restore the cookie as it was set This method is automatically called internally so normally you don't need to call it



public  **delete** ()

Deletes the cookie by setting an expire time in the past



public :doc:`Phalcon\\Http\\Cookie <Phalcon_Http_Cookie>`  **useEncryption** (*boolean* $useEncryption)

Sets if the cookie must be encrypted/decrypted automatically



public *boolean*  **isUsingEncryption** ()

Check if the cookie is using implicit encryption



public :doc:`Phalcon\\Http\\Cookie <Phalcon_Http_Cookie>`  **setExpiration** (*int* $expire)

Sets the cookie's expiration time



public *string*  **getExpiration** ()

Returns the current expiration time



public :doc:`Phalcon\\Http\\Cookie <Phalcon_Http_Cookie>`  **setPath** (*string* $path)

Sets the cookie's expiration time



public *string*  **getPath** ()

Returns the current cookie's path



public :doc:`Phalcon\\Http\\Cookie <Phalcon_Http_Cookie>`  **setDomain** (*string* $domain)

Sets the domain that the cookie is available to



public *string*  **getDomain** ()

Returns the domain that the cookie is available to



public :doc:`Phalcon\\Http\\Cookie <Phalcon_Http_Cookie>`  **setSecure** (*boolean* $secure)

Sets if the cookie must only be sent when the connection is secure (HTTPS)



public *boolean*  **getSecure** ()

Returns whether the cookie must only be sent when the connection is secure (HTTPS)



public :doc:`Phalcon\\Http\\Cookie <Phalcon_Http_Cookie>`  **setHttpOnly** (*boolean* $httpOnly)

Sets if the cookie is accessible only through the HTTP protocol



public *boolean*  **getHttpOnly** ()

Returns if the cookie is accessible only through the HTTP protocol



public *mixed*  **__toString** ()

Magic __toString method converts the cookie's value to string



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


