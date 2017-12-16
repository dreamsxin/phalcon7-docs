Class **Phalcon\\Http\\Client\\Adapter\\Stream**
================================================

*extends* abstract class :doc:`Phalcon\\Http\\Client\\Adapter <Phalcon_Http_Client_Adapter>`

*implements* :doc:`Phalcon\\Http\\Client\\AdapterInterface <Phalcon_Http_Client_AdapterInterface>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/http/client/adapter/stream.c" class="btn btn-default btn-sm">Source on GitHub</a>`




Constants
---------

*string* **VERSION**

*string* **AUTH_TYPE_ANY**

*string* **AUTH_TYPE_BASIC**

*string* **AUTH_TYPE_DIGEST**

Methods
-------

public  **__construct** (*unknown* $uri, *unknown* $method)

...


protected  **buildBody** ()

...


public  **errorHandler** (*unknown* $errno, *unknown* $errstr, *unknown* $errfile, *unknown* $errline, *unknown* $data)

...


protected  **sendInternal** ()

...


public :doc:`Phalcon\\Http\\Client\\Adapter <Phalcon_Http_Client_Adapter>`  **setUserAgent** (*string* $useragent) inherited from Phalcon\\Http\\Client\\Adapter

Sets the value of the userAgent property



public :doc:`Phalcon\\Http\\Client\\Adapter <Phalcon_Http_Client_Adapter>`  **setAuth** (*string* $username, *string* $password, [*string* $authtype], [*array* $digest], [*string* $entityBody]) inherited from Phalcon\\Http\\Client\\Adapter

Set authentication credential



public :doc:`Phalcon\\Http\\Client\\Adapter <Phalcon_Http_Client_Adapter>`  **setHeader** (*string* $name, *string* $value) inherited from Phalcon\\Http\\Client\\Adapter

Set header



public :doc:`Phalcon\\Http\\Client\\Adapter <Phalcon_Http_Client_Adapter>`  **setHeaders** (*array* $headers) inherited from Phalcon\\Http\\Client\\Adapter

Set headers



public :doc:`Phalcon\\Http\\Client\\Adapter <Phalcon_Http_Client_Adapter>`  **setData** (*array|string* $data, [*unknown* $type]) inherited from Phalcon\\Http\\Client\\Adapter

Set data



public :doc:`Phalcon\\Http\\Client\\Adapter <Phalcon_Http_Client_Adapter>`  **setFile** () inherited from Phalcon\\Http\\Client\\Adapter

Set send file



public :doc:`Phalcon\\Http\\Client\\Adapter <Phalcon_Http_Client_Adapter>`  **setFiles** (*array|string* $files) inherited from Phalcon\\Http\\Client\\Adapter

Set send files



public *string*  **getPath** () inherited from Phalcon\\Http\\Client\\Adapter

Retrieve the URI path



public :doc:`Phalcon\\Http\\Client\\Response <Phalcon_Http_Client_Response>`  **get** ([*string* $uri], [*string* $data], [*unknown* $type]) inherited from Phalcon\\Http\\Client\\Adapter

Send GET request



public :doc:`Phalcon\\Http\\Client\\Response <Phalcon_Http_Client_Response>`  **head** ([*string* $uri], [*string* $data], [*unknown* $type]) inherited from Phalcon\\Http\\Client\\Adapter

Send HEAD request



public :doc:`Phalcon\\Http\\Client\\Response <Phalcon_Http_Client_Response>`  **post** ([*string* $uri], [*string* $data], [*unknown* $type]) inherited from Phalcon\\Http\\Client\\Adapter

Send POST request



public :doc:`Phalcon\\Http\\Client\\Response <Phalcon_Http_Client_Response>`  **put** ([*string* $uri], [*string* $data], [*unknown* $type]) inherited from Phalcon\\Http\\Client\\Adapter

Send PUT request



public :doc:`Phalcon\\Http\\Client\\Response <Phalcon_Http_Client_Response>`  **delete** ([*string* $uri], [*string* $data], [*unknown* $type]) inherited from Phalcon\\Http\\Client\\Adapter

Send DELETE request



public :doc:`Phalcon\\Http\\Client\\Adapter <Phalcon_Http_Client_Adapter>`  **setUri** (*string* $uri) inherited from Phalcon\\Http\\Client\\Adapter

Set URI



public :doc:`Phalcon\\Http\\Uri <Phalcon_Http_Uri>`  **getUri** () inherited from Phalcon\\Http\\Client\\Adapter

Get URI



public :doc:`Phalcon\\Http\\Client\\Adapter <Phalcon_Http_Client_Adapter>`  **setBaseUri** ([*string* $uri]) inherited from Phalcon\\Http\\Client\\Adapter

Set base URI



public :doc:`Phalcon\\Http\\Client\\Adapter <Phalcon_Http_Client_Adapter>`  **setMethod** (*unknown* $method) inherited from Phalcon\\Http\\Client\\Adapter

Set method



public :doc:`Phalcon\\Http\\Client\\Adapter <Phalcon_Http_Client_Adapter>`  **setTimeOut** (*unknown* $time) inherited from Phalcon\\Http\\Client\\Adapter

Set the request timeout



public :doc:`Phalcon\\Http\\Client\\Response <Phalcon_Http_Client_Response>`  **send** ([*unknown* $uri]) inherited from Phalcon\\Http\\Client\\Adapter

Send request



