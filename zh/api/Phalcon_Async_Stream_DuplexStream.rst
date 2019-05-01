Interface **Phalcon\\Async\\Stream\\DuplexStream**
==================================================

*implements* :doc:`Phalcon\\Async\\Stream\\ReadableStream <Phalcon_Async_Stream_ReadableStream>`, :doc:`Phalcon\\Async\\Stream\\WritableStream <Phalcon_Async_Stream_WritableStream>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/async/stream/duplexstream.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Methods
-------

abstract public  **getReadableStream** ()

...


abstract public  **getWritableStream** ()

...


abstract public  **close** ([*Throwable* $error]) inherited from Phalcon\\Async\\Stream\\ReadableStream

...


abstract public  **read** ([*unknown* $length]) inherited from Phalcon\\Async\\Stream\\ReadableStream

...


abstract public  **write** (*unknown* $data) inherited from Phalcon\\Async\\Stream\\WritableStream

...


