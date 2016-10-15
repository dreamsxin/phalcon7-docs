HTTP 请求客户端（HTTP Request Client）
======================================
通过 :doc:`Phalcon\\Http\\Client <../api/Phalcon_Http_Client>` 我们可以发起 HTTP 请求。

GET 请求（GET Request）
-----------------------
.. code-block:: php

    <?php

    use Phalcon\Http\Client\Adapter\Curl as Client;

    // Create a client instance
    $client = new Client();

    // Or auto create
    $client = Phalcon\Http\Client::factory();

    // Send GET request
    $response = $client->get('http://localhost/');


POST 请求（POST Request）
-------------------------
.. code-block:: php

    <?php

    use Phalcon\Http\Client\Adapter\Curl as Client;

    // Create a client instance
    $client = new Client();

    // Send POST request
    $response = $client->post('http://localhost/auth/login', array('username' => 'test', 'password' => 'test'));

