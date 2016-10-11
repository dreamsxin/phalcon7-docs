Abstract class **Phalcon\\Http\\Client\\Adapter**
=================================================

*implements* :doc:`Phalcon\\Http\\Client\\AdapterInterface <Phalcon_Http_Client_AdapterInterface>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/phalcon/http/client/adapter.zep" class="btn btn-default btn-sm">Source on GitHub</a>`




Constants
---------

*string* **VERSION**

*string* **AUTH_TYPE_ANY**

*string* **AUTH_TYPE_BASIC**

*string* **AUTH_TYPE_DIGEST**

Methods
-------

public :doc:`Phalcon\\Http\\Client\\Adapter <Phalcon_Http_Client_Adapter>`  **setUserAgent** (*string* $useragent)

Sets the value of the userAgent property



public :doc:`Phalcon\\Http\\Client\\Adapter <Phalcon_Http_Client_Adapter>`  **setAuth** (*string* $username, *string* $password, [*string* $authtype], [*array* $digest], [*string* $entityBody])

Set authentication credential



public :doc:`Phalcon\\Http\\Client\\Adapter <Phalcon_Http_Client_Adapter>`  **setHeader** (*string* $name, *string* $value)

Set header



public :doc:`Phalcon\\Http\\Client\\Adapter <Phalcon_Http_Client_Adapter>`  **setHeaders** (*array* $headers)

Set headers



public :doc:`Phalcon\\Http\\Client\\Adapter <Phalcon_Http_Client_Adapter>`  **setData** (*array|string* $data, [*unknown* $type])

Set data



public :doc:`Phalcon\\Http\\Client\\Adapter <Phalcon_Http_Client_Adapter>`  **setFile** ()

Set send file



public :doc:`Phalcon\\Http\\Client\\Adapter <Phalcon_Http_Client_Adapter>`  **setFiles** (*array|string* $files)

Set send files



public *string*  **getPath** ()

Retrieve the URI path



public :doc:`Phalcon\\Http\\Client\\Response <Phalcon_Http_Client_Response>`  **get** ([*string* $uri], [*string* $data])

Send GET request



public :doc:`Phalcon\\Http\\Client\\Response <Phalcon_Http_Client_Response>`  **head** ([*string* $uri], [*string* $data])

Send HEAD request



public :doc:`Phalcon\\Http\\Client\\Response <Phalcon_Http_Client_Response>`  **post** ([*string* $uri], [*string* $data])

Send POST request



public :doc:`Phalcon\\Http\\Client\\Response <Phalcon_Http_Client_Response>`  **put** ([*string* $uri], [*string* $data])

Send PUT request



public :doc:`Phalcon\\Http\\Client\\Response <Phalcon_Http_Client_Response>`  **delete** ([*string* $uri], [*string* $data])

Send DELETE request



public :doc:`Phalcon\\Http\\Client\\Adapter <Phalcon_Http_Client_Adapter>`  **setUri** (*string* $uri)

Set URI



public :doc:`Phalcon\\Http\\Uri <Phalcon_Http_Uri>`  **getUri** ()

Get URI



public :doc:`Phalcon\\Http\\Client\\Adapter <Phalcon_Http_Client_Adapter>`  **setBaseUri** ([*string* $uri])

Set base URI



public :doc:`Phalcon\\Http\\Client\\Adapter <Phalcon_Http_Client_Adapter>`  **setMethod** (*unknown* $method)

Set method



public :doc:`Phalcon\\Http\\Client\\Adapter <Phalcon_Http_Client_Adapter>`  **setTimeOut** (*unknown* $method)

Set the request timeout



public :doc:`Phalcon\\Http\\Client\\Response <Phalcon_Http_Client_Response>`  **send** ([*unknown* $uri])

Send request



abstract protected  **sendInternal** ()

...


