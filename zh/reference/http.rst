HTTP 请求客户端（HTTP Request Client）
======================================
通过 :doc:`Phalcon\\Http\\Client <../api/Phalcon_Http_Client>` 我们可以发起 HTTP 请求。

.. code-block:: php

    <?php

    use Phalcon\Http\Client\Adapter\Curl as Client;

    // Create a client instance
    $client = new Client();

    // Send GET request
    $response = $client->get('http://localhost/');

