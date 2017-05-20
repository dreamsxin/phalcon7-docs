Class **Phalcon\\Chart\\QRcode**
================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/chart/qrcode.c" class="btn btn-default btn-sm">Source on GitHub</a>`


.. code-block:: php

    <?php

     $qr = new \Phalcon\Chart\QRcode();
     $ret = $qr->generate('Phalcon framework');
     $data = $qr->render();
     $data = $qr->render(NULL, NULL, 'FFCC00', '000000');
     $ret = $qr->save('unit-tests/assets/qr.png');
     $ret = $qr->save('unit-tests/assets/qr.png', NULL, NULL, 'FFCC00', '000000');
     $ret = $qr->scan('unit-tests/assets/qr.png');



Constants
---------

*integer* **MODE_NUL**

*integer* **MODE_NUM**

*integer* **MODE_AN**

*integer* **MODE_8**

*integer* **MODE_KANJI**

*integer* **LEVEL_L**

*integer* **LEVEL_M**

*integer* **LEVEL_Q**

*integer* **LEVEL_H**

Methods
-------

public  **__construct** ()

Phalcon\\Chart\\QRcode constructor $qr = new \\Phalcon\\Chart\\QRcode; $qr->generate('Phalcon is a web framework', 4, \\Phalcon\\Chart\\QRcode::LEVEL_L, \\Phalcon\\Chart\\QRcode::MODE_KANJI, TRUE); $qr->save('qr.png');



public *boolean*  **generate** (*string* $text, [*int* $version], [*int* $level], [*int* $mode], [*boolean* $casesensitive])

Generate QR data



public *string*  **render** ([*int* $size], [*unknown* $margin], [*string* $foreground], [*string* $background])

Render the image and return the binary string. $qr = new \\Phalcon\\Chart\\QRcode; $qr->generate('Phalcon is a web framework'); $data = \\Phalcon\\Chart\\QRcode::render();



public *boolean*  **save** (*filename* $filename, [*size* $size], [*unknown* $margin], [*unknown* $foreground], [*unknown* $background])

Save the image $qr = new \\Phalcon\\Chart\\QRcode; $qr->generate('Phalcon is a web framework', 4, \\Phalcon\\Chart\\QRcode::LEVEL_L, \\Phalcon\\Chart\\QRcode::MODE_KANJI, TRUE); $qr->save('qr.png');



public *string*  **scan** (*string* $filename)

Scan the image. $qr = new \\Phalcon\\Chart\\QRcode; $ret = $qr->san('qr.png');



