Class **Phalcon\\JsonRpc\\Client**
==================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/phalcon/jsonrpc/client.zep" class="btn btn-default btn-sm">Source on GitHub</a>`


.. code-block:: php

    <?php

    $httpclient = new Phalcon\Http\Client\Adapter\Stream('http://rpc.edu.local');
    $rpc = new Phalcon\JsonRpc\Client($httpclient);
    $rpc->call('auth/sigup', array('username' => 'phalcon', 'password' => 'Hello:)'));



Methods
-------

public  **__construct** (*unknown* $httpclient)

...


public *Phalcon\\JsonRpc\\Response*  **call** (*string* $method, [*unknown* $params])

Rpc call



