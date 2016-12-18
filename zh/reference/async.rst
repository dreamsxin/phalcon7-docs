异步调用（Asynchronous）
========================
通过 :doc:`Phalcon\\Async <../api/Phalcon_Async>` 我们可以异步调用方法。

异步调用（Called asynchronous）
-------------------------------
.. code-block:: php

    <?php

    $id1 = Phalcon\Async::call(function () {
        return 'one1';
    });
    $id2 = Phalcon\Async::call(function () {
        return 'one2';
    });

获取异步调用结果个数（Gets result count）
-----------------------------------------
.. code-block:: php

    <?php

    $num = Phalcon\Async::count();

获取异步调用结果（Gets asynchronous result）
--------------------------------------------
.. code-block:: php

    <?php

    $ret = Phalcon\Async::recv($id1);
    $rets = Phalcon\Async::recvAll();
