分布式自增 ID（Snowflake）
==========================
Phalcon 提供了 :doc:`Phalcon\\Snowflake <../api/Phalcon_Snowflake>` 类来生成自增ID。

.. code-block:: php

    <?php

    $snowflake = new Phalcon\Snowflake;
    $id = $snowflake->nextId();
    $desc = $snowflake->parse($id)
