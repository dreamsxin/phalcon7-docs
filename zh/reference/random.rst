随机数（Random）
================
Phalcon 提供了 :doc:`Phalcon\\Random <../api/Phalcon_Random>` 与 :doc:`Phalcon\\Security\\Random <../api/Phalcon_Security_Random>` 类来生成随机数。

.. code-block:: php

    <?php

    $random = new \Phalcon\Random();
    $alnum = $random->alnum();