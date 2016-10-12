Interface **Phalcon\\Http\\Client\\AdapterInterface**
=====================================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/http/client/adapterinterface.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Phalcon\\Http\\Client\\AdapterInterface initializer


Methods
-------

abstract public  **setUserAgent** (*unknown* $useragent)

...


abstract public  **setAuth** (*unknown* $username, *unknown* $password, [*unknown* $authtype], [*unknown* $digest], [*unknown* $entityBody])

...


abstract public  **setHeader** (*unknown* $name, *unknown* $value)

...


abstract public  **setHeaders** (*unknown* $headers)

...


abstract public  **setData** (*unknown* $data, [*unknown* $type])

...


abstract public  **setFiles** (*unknown* $files)

...


abstract public  **get** ([*unknown* $uri], [*unknown* $data])

...


abstract public  **head** ([*unknown* $uri], [*unknown* $data])

...


abstract public  **post** ([*unknown* $uri], [*unknown* $data])

...


abstract public  **put** ([*unknown* $uri], [*unknown* $data])

...


abstract public  **delete** ([*unknown* $uri], [*unknown* $data])

...


abstract public  **setUri** (*unknown* $uri)

...


abstract public  **getUri** ()

...


abstract public  **setBaseUri** ([*unknown* $uri])

...


abstract public  **setMethod** (*unknown* $method)

...


abstract public  **setTimeOut** (*unknown* $time)

...


abstract public  **send** ([*unknown* $uri])

...


