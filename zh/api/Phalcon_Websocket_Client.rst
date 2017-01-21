Class **Phalcon\\Websocket\\Client**
====================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/websocket/client.c" class="btn btn-default btn-sm">Source on GitHub</a>`


.. code-block:: php

    <?php

     $client = new Phalcon\Websocket\Client('127.0.0.1', 8080);
     $client->on(Phalcon\Websocket\Client::ON_ACCEPT, function($client, $conn){
         echo 'Accept'.PHP_EOL;
     });
     $client->on(Phalcon\Websocket\Client::ON_CLOSE, function(){
         echo 'Close'.PHP_EOL;
     });
     $client->on(Phalcon\Websocket\Client::ON_DATA, function($client, $conn){
         echo 'Data'.PHP_EOL;
     });
     $client->connect();
    <／code>



Constants
---------

*integer* **ON_ACCEPT**

*integer* **ON_CLOSE**

*integer* **ON_DATA**

*integer* **ON_TICK**

Methods
-------

public  **__construct** (*string* $host, [*int* $port], [*unknown* $path])

Phalcon\\Websocket\\Client constructor



public  **on** (*unknown* $event, *unknown* $callback)

Register a callback for specified event



public  **connect** ([*unknown* $accept], [*unknown* $close], [*unknown* $data], [*unknown* $tick])

Establish connection with remote server



public  **send** (*unknown* $text)

Send data to the client



public  **sendJson** (*unknown* $payload)

Send data to the client as JSON string



public  **isConnected** ()

Check is connection is established



public  **disconnect** ()

Close connection to the client



