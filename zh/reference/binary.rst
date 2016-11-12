二进制数据读取与写入（Binary Data Read And Writer）
===================================================
二进制数据组件给应用提供二进制数据读取、写入等功能，内部使用 `pack`、`unpack` 函数实现。

二进制数据读取（Binary Data Read）
----------------------------------
示例：

.. code-block:: php

    <?php

    $fp = fopen('test.bin', 'rb');

    $bin = new Phalcon\Binary\Reader($fp);
    $flag = $bin->readUnsignedChar();
    $num = $bin->readUnsignedInt16();
    $name = $bin->readString();


二进制数据写入（Binary Data Read）
----------------------------------
示例：

.. code-block:: php

    <?php

    $fp = fopen('test.bin', 'wb');

    $bin = new Phalcon\Binary\Write($fp);
    $bin->writeUnsignedChar(1);
    $bin->writeUnsignedInt16(240);
    $bin->writeString('Phalcon7');
