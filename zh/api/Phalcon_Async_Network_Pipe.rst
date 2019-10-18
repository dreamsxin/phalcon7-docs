Final class **Phalcon\\Async\\Network\\Pipe**
=============================================

*implements* :doc:`Phalcon\\Async\\Network\\SocketStream <Phalcon_Async_Network_SocketStream>`, :doc:`Phalcon\\Async\\Stream\\ReadableStream <Phalcon_Async_Stream_ReadableStream>`, :doc:`Phalcon\\Async\\Stream\\WritableStream <Phalcon_Async_Stream_WritableStream>`, :doc:`Phalcon\\Async\\Stream\\DuplexStream <Phalcon_Async_Stream_DuplexStream>`, :doc:`Phalcon\\Async\\Network\\Socket <Phalcon_Async_Network_Socket>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/async/network/pipe.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Methods
-------

private  **__construct** ()

...


public  **__wakeup** ()

...


public static  **connect** (*unknown* $name, [*unknown* $host], [*unknown* $ipc])

...


public static  **import** (:doc:`Phalcon\\Async\\Network\\Pipe <Phalcon_Async_Network_Pipe>` $pipe, [*unknown* $ipc])

...


public static  **pair** ([*unknown* $ipc])

...


public  **close** ([*Throwable* $error])

...


public  **flush** ()

...


public  **getAddress** ()

...


public  **getPort** ()

...


public  **setOption** (*unknown* $option, *unknown* $value)

...


public  **getRemoteAddress** ()

...


public  **getRemotePort** ()

...


public  **isAlive** ()

...


public  **read** ([*unknown* $length])

...


public  **getReadableStream** ()

...


public  **write** (*unknown* $data)

...


public  **getWriteQueueSize** ()

...


public  **getWritableStream** ()

...


public  **export** (:doc:`Phalcon\\Async\\Network\\Pipe <Phalcon_Async_Network_Pipe>` $pipe)

...


