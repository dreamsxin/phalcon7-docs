Class **Phalcon\\Http\\Request**
================================

*extends* abstract class :doc:`Phalcon\\Di\\Injectable <Phalcon_Di_Injectable>`

*implements* :doc:`Phalcon\\Events\\EventsAwareInterface <Phalcon_Events_EventsAwareInterface>`, :doc:`Phalcon\\Di\\InjectionAwareInterface <Phalcon_Di_InjectionAwareInterface>`, :doc:`Phalcon\\Http\\RequestInterface <Phalcon_Http_RequestInterface>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/http/request.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Encapsulates request information for easy and secure access from application controllers.    The request object is a simple value object that is passed between the dispatcher and controller classes. It packages the HTTP request environment.    

.. code-block:: php

    <?php

    $request = new Phalcon\Http\Request();
    if ($request->isPost() == true) {
    	if ($request->isAjax() == true) {
    		echo 'Request was made using POST and AJAX';
    	}
    }



Methods
-------

public  **__construct** ()

Phalcon\\Http\\Request constructor



protected *mixed*  **_get** (*array* $data, *string* $name, *string|array* $filters, *mixed* $defaultValue, *boolean* $notAllowEmpty, *boolean* $noRecursive)

Internal get wrapper to filter



public *mixed*  **get** ([*string* $name], [*string|array* $filters], [*mixed* $defaultValue], [*boolean* $notAllowEmpty], [*boolean* $noRecursive])

Gets a variable from the $_REQUEST superglobal applying filters if needed. If no parameters are given the $_REQUEST superglobal is returned 

.. code-block:: php

    <?php

    //Returns value from $_REQUEST["user_email"] without sanitizing
    $userEmail = $request->get("user_email");
    
    //Returns value from $_REQUEST["user_email"] with sanitizing
    $userEmail = $request->get("user_email", "email");




public *mixed*  **getPost** ([*string* $name], [*string|array* $filters], [*mixed* $defaultValue], [*boolean* $notAllowEmpty], [*boolean* $noRecursive])

Gets a variable from the $_POST superglobal applying filters if needed If no parameters are given the $_POST superglobal is returned 

.. code-block:: php

    <?php

    //Returns value from $_POST["user_email"] without sanitizing
    $userEmail = $request->getPost("user_email");
    
    //Returns value from $_POST["user_email"] with sanitizing
    $userEmail = $request->getPost("user_email", "email");




public *mixed*  **getPut** ([*string* $name], [*string|array* $filters], [*mixed* $defaultValue], [*boolean* $notAllowEmpty], [*boolean* $noRecursive])

Gets a variable from put request 

.. code-block:: php

    <?php

    $userEmail = $request->getPut("user_email");
    
    $userEmail = $request->getPut("user_email", "email");




public *mixed*  **getQuery** ([*string* $name], [*string|array* $filters], [*mixed* $defaultValue], [*boolean* $notAllowEmpty], [*boolean* $noRecursive])

Gets variable from $_GET superglobal applying filters if needed If no parameters are given the $_GET superglobal is returned 

.. code-block:: php

    <?php

    //Returns value from $_GET["id"] without sanitizing
    $id = $request->getQuery("id");
    
    //Returns value from $_GET["id"] with sanitizing
    $id = $request->getQuery("id", "int");
    
    //Returns value from $_GET["id"] with a default value
    $id = $request->getQuery("id", null, 150);




public *mixed*  **getServer** (*string* $name)

Gets variable from $_SERVER superglobal



public *string|boolean*  **getEnv** (*string* $name)

Gets the value of an environment variable



public *mixed*  **getParam** (*unknown* $name, [*string|array* $filters], [*mixed* $defaultValue])

Gets a param by its name or numeric index



public *boolean*  **has** (*string* $name)

Checks whether $_REQUEST superglobal has certain index



public *boolean*  **hasPost** (*string* $name)

Checks whether $_POST superglobal has certain index



public *boolean*  **hasPut** (*string* $name)

Checks whether put has certain index



public *boolean*  **hasQuery** (*string* $name)

Checks whether $_GET superglobal has certain index



public *mixed*  **hasServer** (*string* $name)

Checks whether $_SERVER superglobal has certain index



public *string*  **hasHeader** (*string* $header)

Checks whether $_SERVER superglobal has certain index



public *string*  **getHeader** (*string* $header)

Gets HTTP header from request data



public *string*  **getScheme** ()

Gets HTTP schema (http/https)



public *boolean*  **isAjax** ()

Checks whether request has been made using ajax. Checks if $_SERVER['HTTP_X_REQUESTED_WITH']=='XMLHttpRequest'



public *boolean*  **isSoapRequested** ()

Checks whether request has been made using SOAP



public *boolean*  **isSecureRequest** ()

Checks whether request has been made using any secure layer



public *string*  **getRawBody** ()

Gets HTTP raw request body



public *string*  **getJsonRawBody** ()

Gets decoded JSON HTTP raw request body



public *string*  **getBsonRawBody** ()

Gets decoded BSON HTTP raw request body



public *string*  **getServerAddress** ()

Gets active server address IP



public *string*  **getServerName** ()

Gets active server name



public *string*  **getHttpHost** ()

Gets information about schema, host and port used by the request



public *string*  **getClientAddress** ([*boolean* $trustForwardedHeader])

Gets most possible client IPv4 Address. This method search in $_SERVER['REMOTE_ADDR'] and optionally in $_SERVER['HTTP_X_FORWARDED_FOR']



public *string*  **getMethod** ()

Gets HTTP method which request has been made



public *string*  **getURI** ()

Gets HTTP URI which request has been made



public *string*  **getQueryString** ()

Gets query string which request has been made



public *string*  **getUserAgent** ()

Gets HTTP user agent used to made the request



public *boolean*  **isMethod** (*string|array* $methods)

Check if HTTP method match any of the passed methods



public *boolean*  **isPost** ()

Checks whether HTTP method is POST. if $_SERVER['REQUEST_METHOD']=='POST'



public *boolean*  **isGet** ()

Checks whether HTTP method is GET. if $_SERVER['REQUEST_METHOD']=='GET'



public *boolean*  **isPut** ()

Checks whether HTTP method is PUT. if $_SERVER['REQUEST_METHOD']=='PUT'



public *boolean*  **isPatch** ()

Checks whether HTTP method is PATCH. if $_SERVER['REQUEST_METHOD']=='PATCH'



public *boolean*  **isHead** ()

Checks whether HTTP method is HEAD. if $_SERVER['REQUEST_METHOD']=='HEAD'



public *boolean*  **isDelete** ()

Checks whether HTTP method is DELETE. if $_SERVER['REQUEST_METHOD']=='DELETE'



public *boolean*  **isOptions** ()

Checks whether HTTP method is OPTIONS. if $_SERVER['REQUEST_METHOD']=='OPTIONS'



public *boolean*  **hasFiles** ([*unknown* $notErrored])

Checks whether request includes attached files



public :doc:`Phalcon\\Http\\Request\\File <Phalcon_Http_Request_File>` [] **getUploadedFiles** ([*boolean* $notErrored], [*string* $index])

Gets attached files as Phalcon\\Http\\Request\\File instances



public *array*  **getHeaders** ()

Returns the available headers in the request



public *string*  **getHTTPReferer** ()

Gets web page that refers active request. ie: http://www.google.com



protected *array*  **_getQualityHeader** ()

Process a request header and return an array of values with their qualities



protected *string*  **_getBestQuality** ()

Process a request header and return the one with best quality



public *array*  **getAcceptableContent** ()

Gets array with mime/types and their quality accepted by the browser/client from $_SERVER['HTTP_ACCEPT']



public *array*  **getBestAccept** ()

Gets best mime/type accepted by the browser/client from $_SERVER['HTTP_ACCEPT']



public *array*  **getClientCharsets** ()

Gets charsets array and their quality accepted by the browser/client from $_SERVER['HTTP_ACCEPT_CHARSET']



public *string*  **getBestCharset** ()

Gets best charset accepted by the browser/client from $_SERVER['HTTP_ACCEPT_CHARSET']



public *array*  **getLanguages** ()

Gets languages array and their quality accepted by the browser/client from $_SERVER['HTTP_ACCEPT_LANGUAGE']



public *string*  **getBestLanguage** ()

Gets best language accepted by the browser/client from $_SERVER['HTTP_ACCEPT_LANGUAGE']



public *array*  **getBasicAuth** ()

Gets auth info accepted by the browser/client from $_SERVER['PHP_AUTH_USER']



public *array*  **getDigestAuth** ()

Gets auth info accepted by the browser/client from $_SERVER['PHP_AUTH_DIGEST']



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


