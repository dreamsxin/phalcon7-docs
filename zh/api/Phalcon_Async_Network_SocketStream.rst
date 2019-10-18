Interface **Phalcon\\Async\\Network\\SocketStream**
===================================================

*implements* :doc:`Phalcon\\Async\\Network\\Socket <Phalcon_Async_Network_Socket>`, :doc:`Phalcon\\Async\\Stream\\DuplexStream <Phalcon_Async_Stream_DuplexStream>`, :doc:`Phalcon\\Async\\Stream\\WritableStream <Phalcon_Async_Stream_WritableStream>`, :doc:`Phalcon\\Async\\Stream\\ReadableStream <Phalcon_Async_Stream_ReadableStream>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/async/network/socketstream.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Methods
-------

abstract public  **getRemoteAddress** ()

...


abstract public  **getRemotePort** ()

...


abstract public  **isAlive** ()

...


abstract public  **flush** ()

...


abstract public  **getWriteQueueSize** ()

...


abstract public  **close** ([*Throwable* $error]) inherited from Phalcon\\Async\\Network\\Socket

...


abstract public  **getAddress** () inherited from Phalcon\\Async\\Network\\Socket

...


abstract public  **getPort** () inherited from Phalcon\\Async\\Network\\Socket

...


abstract public  **setOption** (*unknown* $option, *unknown* $value) inherited from Phalcon\\Async\\Network\\Socket

...


abstract public  **getReadableStream** () inherited from Phalcon\\Async\\Stream\\DuplexStream

...


abstract public  **getWritableStream** () inherited from Phalcon\\Async\\Stream\\DuplexStream

...


abstract public  **read** ([*unknown* $length]) inherited from Phalcon\\Async\\Stream\\ReadableStream

...


abstract public  **write** (*unknown* $data) inherited from Phalcon\\Async\\Stream\\WritableStream

...


