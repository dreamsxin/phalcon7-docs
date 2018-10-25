二进制数据读取与写入（Binary Data Read And Write）
==================================================
二进制数据组件给应用提供二进制数据读取、写入等功能，内部使用 `pack`、`unpack` 函数实现。

二进制数据读取（Binary Data Read）
----------------------------------
二进制读取相关方法请查看 :doc:`Phalcon\\Binary\\Reader <../api/Phalcon_Binary_Reader>` 示例：

.. code-block:: php

    <?php

    $fp = fopen('test.bin', 'rb');

    $bin = new Phalcon\Binary\Reader($fp, Phalcon\Binary::MACHINE);
    $flag = $bin->readUnsignedChar();
    $num = $bin->readUnsignedInt16();
    $name = $bin->readString();

    // 大端，高位在前
    $bin = new Phalcon\Binary\Writer(NULL, Phalcon\Binary::ENDIAN_BIG);
    $bin->writeUnsignedChar(1);
    $bin->writeUnsignedInt16(240);
    $bin->writeString('Phalcon7');
    $data = $bin->getContent();

    $bin = new Phalcon\Binary\Reader($data, Phalcon\Binary::ENDIAN_BIG);
    echo $bin->readUnsignedChar().PHP_EOL;
    echo $bin->readUnsignedInt16().PHP_EOL;
    echo $bin->readString().PHP_EOL;


二进制数据写入（Binary Data Write）
-----------------------------------
二进制写入相关方法请查看 :doc:`Phalcon\\Binary\\Writer <../api/Phalcon_Binary_Writer>` 示例：

.. code-block:: php

    <?php

    $fp = fopen('test.bin', 'wb');

    $bin = new Phalcon\Binary\Writer($fp, Phalcon\Binary::MACHINE);
    $bin->writeUnsignedChar(1);
    $bin->writeUnsignedInt16(240);
    $bin->writeString('Phalcon7');

