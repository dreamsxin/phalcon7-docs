Abstract class **Phalcon\\Server**
==================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/server.c" class="btn btn-default btn-sm">Source on GitHub</a>`

It‘s an implementation of the socket server


Methods
-------

public  **__construct** (*array* $config)

Phalcon\\Server constructor



public  **start** ()

Run the Server



public *boolean*  **close** (*int* $fd)

Close the socket



abstract public  **onConnect** (*int* $fd)

Emitted when the socket has connected



abstract public  **onReceive** (*int* $fd, *string* $data)

Emitted when the socket has received



abstract public  **onSend** (*int* $fd)

Emitted when the socket has send



abstract public  **onClose** (*int* $fd)

Emitted when the socket has closed



