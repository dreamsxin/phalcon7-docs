Class **Phalcon\\Chart\\Captcha**
=================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/chart/captcha.c" class="btn btn-default btn-sm">Source on GitHub</a>`


.. code-block:: php

    <?php

     header('Content-Type: image/png');
     $captcha = new \Phalcon\Chart\Captcha(NULL, NULL, 30, 150, 50);
     echo $captcha = $captcha->render('Phalcon', 15, -10);



Methods
-------

public  **__construct** ()

Phalcon\\Chart\\Captcha constructor $captcha = new \\Phalcon\\Chart\\Captcha; $captcha->generate('Phalcon is a web framework'); $captcha->save('qr.png');



public *boolean*  **setFont** (*string* $font)

Sets a font



public *boolean*  **setFontSize** (*unknown* $size)

Sets a font size



public *String*  **render** (*string* $word, [*string* $margin], [*unknown* $foreground], [*unknown* $background])

Generate Captcha data 

.. code-block:: php

    <?php

         $captcha = new \Phalcon\Chart\Captcha;
         $captcha->reander('Phalcon is a web framework');




public *boolean*  **save** ([*filename* $filename])

Save the image 

.. code-block:: php

    <?php

         $captcha = new \Phalcon\Chart\Captcha;
         $captcha->reander('Phalcon is a web framework');
         $captcha->save('captcha.png');




