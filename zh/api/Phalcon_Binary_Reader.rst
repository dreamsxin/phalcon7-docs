Class **Phalcon\\Binary\\Reader**
=================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/binary/reader.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Provides utilities to work with binary data  

.. code-block:: php

    <?php

    $fp = fopen('unit-tests/assets/data.bin', 'rb');
    $bin = new Phalcon\Binary\Reader($fp);
    $v = $bin->readUnsignedChar();



Methods
-------

public  **__construct** (*string|resource* $data, [*int* $endian])

Phalcon\\Binary\\Reader constructor



public *int*  **getEndian** ()

Gets the endian



public *int*  **getInput** ()

Gets the input



public *int*  **getContent** ()

Gets the binary data



public *boolean*  **setPosition** (*integer* $position, [*integer* $whence])

Sets the position in the the file pointer



public *int*  **getPosition** ()

Gets the current postion in the the file pointer



public *int*  **getEofPosition** ()

Gets the eof postion the file pointer



public *boolean*  **isEof** ()

Checks if end of the file pointer was reached



public *string*  **read** (*integer* $length)

Read num bytes from the current position in the file pointer



public *string*  **readChar** ()

Read a signed char from the current position in the file pointer



public *string*  **readUnsignedChar** ()

Read a unsigned char from the current position in the file pointer



public *int*  **readInt16** ()

Read a signed short int from the current position in the file pointer



public *int*  **readUnsignedInt16** ([*unknown* $endian])

Read a unsigned short int from the current position in the file pointer



public *int*  **readInt** ()

Read a signed int from the current position in the file pointer



public *int*  **readUnsignedInt** ()

Read a unsigned int from the current position in the file pointer



public *int*  **readInt32** ()

Read a signed long int from the current position in the file pointer



public *int*  **readUnsignedInt32** ([*unknown* $endian])

Read a unsigned long int from the current position in the file pointer



public *float*  **readFloat** ()

Read a float from the current position in the file pointer



public *double*  **readDouble** ()

Read a double from the current position in the file pointer



public *string*  **readString** ([*unknown* $length])

Read string from the current position in the file pointer



public *string*  **readHexString** ([*unknown* $length], [*unknown* $lowNibble])

Read hex string from the current position in the file pointer



