Class **Phalcon\\Chart\\Captcha**
=================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/chart/captcha.c" class="btn btn-default btn-sm">Source on GitHub</a>`


.. code-block:: php

    <?php

     header('Content-Type: image/png');
     $captcha = new \Phalcon\Chart\Captcha(Phalcon\Text::random(Phalcon\Text::RANDOM_ALNUM, 4), NULL, 30, 150, 50);
     echo $captcha = $captcha->render();



Constants
---------

*integer* **PAD_BOTH**

*integer* **PAD_LEFT**

*integer* **PAD_RIGHT**

Methods
-------

public  **__construct** ([*unknown* $word], [*unknown* $font], [*unknown* $fontSize], [*unknown* $width], [*unknown* $height], [*unknown* $pad_size], [*unknown* $pad_type])

Phalcon\\Chart\\Captcha constructor $captcha = new \\Phalcon\\Chart\\Captcha; $captcha->generate('Phalcon is a web framework'); $captcha->save('qr.png');



public *boolean*  **setFont** (*string* $font)

Sets a font



public *boolean*  **setFontSize** (*unknown* $size)

Sets a font size



public *String*  **render** ([*unknown* $filename], [*string* $word], [*unknown* $offset_x], [*unknown* $offset_y], [*unknown* $foreground], [*unknown* $background], [*unknown* $width], [*unknown* $height])

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




