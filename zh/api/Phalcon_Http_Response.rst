Class **Phalcon\\Http\\Response**
=================================

*extends* abstract class :doc:`Phalcon\\Di\\Injectable <Phalcon_Di_Injectable>`

*implements* :doc:`Phalcon\\Events\\EventsAwareInterface <Phalcon_Events_EventsAwareInterface>`, :doc:`Phalcon\\Di\\InjectionAwareInterface <Phalcon_Di_InjectionAwareInterface>`, :doc:`Phalcon\\Http\\ResponseInterface <Phalcon_Http_ResponseInterface>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/http/response.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Part of the HTTP cycle is return responses to the clients. Phalcon\\HTTP\\Response is the Phalcon component responsible to achieve this task. HTTP responses are usually composed by headers and body.  

.. code-block:: php

    <?php

    $response = new Phalcon\Http\Response();
    $response->setStatusCode(200, "OK");
    $response->setContent("<html><body>Hello</body></html>");
    $response->send();



Methods
-------

public  **__construct** ([*string* $content], [*int* $code], [*string* $status])

Phalcon\\Http\\Response constructor



public :doc:`Phalcon\\Http\\ResponseInterface <Phalcon_Http_ResponseInterface>`  **setStatusCode** (*int* $code, *string* $message)

Sets the HTTP response code 

.. code-block:: php

    <?php

    $response->setStatusCode(404, "Not Found");




public :doc:`Phalcon\\Http\\ResponseInterface <Phalcon_Http_ResponseInterface>`  **setHeaders** (:doc:`Phalcon\\Http\\Response\\HeadersInterface <Phalcon_Http_Response_HeadersInterface>` $headers)

Sets a headers bag for the response externally



public :doc:`Phalcon\\Http\\Response\\HeadersInterface <Phalcon_Http_Response_HeadersInterface>`  **getHeaders** ()

Returns headers set by the user



public :doc:`Phalcon\\Http\\ResponseInterface <Phalcon_Http_ResponseInterface>`  **setCookies** (:doc:`Phalcon\\Http\\Response\\CookiesInterface <Phalcon_Http_Response_CookiesInterface>` $cookies)

Sets a cookies bag for the response externally



public :doc:`Phalcon\\Http\\Response\\CookiesInterface <Phalcon_Http_Response_CookiesInterface>`  **getCookies** ()

Returns coookies set by the user



public :doc:`Phalcon\\Http\\ResponseInterface <Phalcon_Http_ResponseInterface>`  **setHeader** (*string* $name, *string* $value)

Overwrites a header in the response 

.. code-block:: php

    <?php

    $response->setHeader("Content-Type", "text/plain");




public :doc:`Phalcon\\Http\\ResponseInterface <Phalcon_Http_ResponseInterface>`  **setRawHeader** (*string* $header)

Send a raw header to the response 

.. code-block:: php

    <?php

    $response->setRawHeader("HTTP/1.1 404 Not Found");




public :doc:`Phalcon\\Http\\ResponseInterface <Phalcon_Http_ResponseInterface>`  **resetHeaders** ()

Resets all the stablished headers



public :doc:`Phalcon\\Http\\ResponseInterface <Phalcon_Http_ResponseInterface>`  **setExpires** (*\DateTime* $datetime)

Sets a Expires header to use HTTP cache 

.. code-block:: php

    <?php

    $this->response->setExpires(new DateTime());




public :doc:`Phalcon\\Http\\ResponseInterface <Phalcon_Http_ResponseInterface>`  **setNotModified** ()

Sends a Not-Modified response



public :doc:`Phalcon\\Http\\ResponseInterface <Phalcon_Http_ResponseInterface>`  **setContentType** (*string* $contentType, [*string* $charset])

Sets the response content-type mime, optionally the charset 

.. code-block:: php

    <?php

    $response->setContentType('application/pdf');
    $response->setContentType('text/plain', 'UTF-8');




public  **setEtag** (*string* $etag)

Set a custom ETag 

.. code-block:: php

    <?php

    $response->setEtag(md5(time()));




public :doc:`Phalcon\\Http\\ResponseInterface <Phalcon_Http_ResponseInterface>`  **redirect** ([*string|array* $location], [*boolean* $externalRedirect], [*int* $statusCode])

Redirect by HTTP to another action or URL 

.. code-block:: php

    <?php

      //Using a string redirect (internal/external)
    $response->redirect("posts/index");
    $response->redirect("http://en.wikipedia.org", true);
    $response->redirect("http://www.example.com/new-location", true, 301);
    
    //Making a redirection based on a named route
    $response->redirect(array(
    	"for" => "index-lang",
    	"lang" => "jp",
    	"controller" => "index"
    ));




public :doc:`Phalcon\\Http\\ResponseInterface <Phalcon_Http_ResponseInterface>`  **setContent** (*string* $content)

Sets HTTP response body 

.. code-block:: php

    <?php

    $response->setContent("<h1>Hello!</h1>");




public :doc:`Phalcon\\Http\\ResponseInterface <Phalcon_Http_ResponseInterface>`  **setJsonContent** (*string* $content)

Sets HTTP response body. The parameter is automatically converted to JSON 

.. code-block:: php

    <?php

    $response->setJsonContent(array("status" => "OK"));
    $response->setJsonContent(array("status" => "OK"), JSON_NUMERIC_CHECK);

*



public :doc:`Phalcon\\Http\\ResponseInterface <Phalcon_Http_ResponseInterface>`  **setBsonContent** (*mixed* $content)

Sets HTTP response body. The parameter is automatically converted to BSON 

.. code-block:: php

    <?php

    $response->setBsonContent(array("status" => "OK", "pic" => new MongoBinData(file_get_contents("/var/www/phalconphp.jpg")));

*



public :doc:`Phalcon\\Http\\ResponseInterface <Phalcon_Http_ResponseInterface>`  **appendContent** (*string* $content)

Appends a string to the HTTP response body



public *string*  **getContent** ()

Gets the HTTP response body



public *boolean*  **isSent** ()

Check if the response is already sent



public :doc:`Phalcon\\Http\\ResponseInterface <Phalcon_Http_ResponseInterface>`  **sendHeaders** ()

Sends headers to the client



public :doc:`Phalcon\\Http\\ResponseInterface <Phalcon_Http_ResponseInterface>`  **sendCookies** ()

Sends cookies to the client



public :doc:`Phalcon\\Http\\ResponseInterface <Phalcon_Http_ResponseInterface>`  **send** ()

Prints out HTTP response to the client



public  **setFileToSend** (*string* $filePath, [*string* $attachmentName])

Sets an attached file to be sent at the end of the request



public  **__toString** ()

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


