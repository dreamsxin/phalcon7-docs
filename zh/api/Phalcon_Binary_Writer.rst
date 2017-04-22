Class **Phalcon\\Binary\\Writer**
=================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/binary/writer.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Provides utilities to work with binary data  

.. code-block:: php

    <?php

    $fp = fopen('unit-tests/assets/data.bin', 'wb');
    $bin = new Phalcon\Binary\Writer($fp);
    $bin->writeUnsignedChar(1);



Methods
-------

public  **__construct** ([*string|resource* $data], [*int* $endian])

Phalcon\\Binary\\Writer constructor



public *int*  **getEndian** ()

Gets the endian



public *int*  **getOutput** ()

Gets the ouput



public *int*  **getContent** ()

Gets the ouput



public *int*  **getPosition** ()

Gets the current postion



public :doc:`Phalcon\\Binary\\Writer <Phalcon_Binary_Writer>`  **write** (*unknown* $data, *unknown* $length)

Write bytes to the current position in the file pointer



public :doc:`Phalcon\\Binary\\Writer <Phalcon_Binary_Writer>`  **writeChar** (*unknown* $byte)

Write a signed char to the current position in the file pointer



public :doc:`Phalcon\\Binary\\Writer <Phalcon_Binary_Writer>`  **writeUnsignedChar** (*unknown* $byte)

Write a unsigned char to the current position in the file pointer



public :doc:`Phalcon\\Binary\\Writer <Phalcon_Binary_Writer>`  **writeInt16** (*unknown* $num)

Write a signed short int to the current position in the file pointer



public :doc:`Phalcon\\Binary\\Writer <Phalcon_Binary_Writer>`  **writeUnsignedInt16** (*unknown* $num, [*unknown* $endian])

Write a unsigned short int to the current position in the file pointer



public :doc:`Phalcon\\Binary\\Writer <Phalcon_Binary_Writer>`  **writeInt** (*unknown* $num)

Write a signed int to the current position in the file pointer



public :doc:`Phalcon\\Binary\\Writer <Phalcon_Binary_Writer>`  **writeUnsignedInt** (*unknown* $num)

Write a unsigned int to the current position in the file pointer



public :doc:`Phalcon\\Binary\\Writer <Phalcon_Binary_Writer>`  **writeInt32** (*unknown* $num)

Write a signed long int to the current position in the file pointer



public :doc:`Phalcon\\Binary\\Writer <Phalcon_Binary_Writer>`  **writeUnsignedInt32** (*unknown* $num, [*unknown* $endian])

Write a unsigned long int to the current position in the file pointer



public :doc:`Phalcon\\Binary\\Writer <Phalcon_Binary_Writer>`  **writeFloat** (*unknown* $num)

Write a float to the current position in the file pointer



public :doc:`Phalcon\\Binary\\Writer <Phalcon_Binary_Writer>`  **writeDouble** (*unknown* $num)

Write a double to the current position in the file pointer



public :doc:`Phalcon\\Binary\\Writer <Phalcon_Binary_Writer>`  **writeString** (*unknown* $str, [*unknown* $length], [*unknown* $exact])

Write string to the current position in the file pointer



public :doc:`Phalcon\\Binary\\Writer <Phalcon_Binary_Writer>`  **writeHexString** (*unknown* $str, [*unknown* $length], [*unknown* $lowNibble])

Write hex string to the current position in the file pointer



