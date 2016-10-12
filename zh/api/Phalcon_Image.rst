Abstract class **Phalcon\\Image**
=================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/image.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Image manipulation support. Allows images to be resized, cropped, etc.  

.. code-block:: php

    <?php

    $image = Phalcon\Image::factory("upload/test.jpg");
    $image->resize(200, 200);
    $image->save();



Constants
---------

*integer* **NONE**

*integer* **WIDTH**

*integer* **HEIGHT**

*integer* **AUTO**

*integer* **INVERSE**

*integer* **PRECISE**

*integer* **TENSILE**

*integer* **NARROW**

*integer* **HORIZONTAL**

*integer* **VERTICAL**

*integer* **GD**

*integer* **IMAGICK**

Methods
-------

public static  **factory** (*unknown* $file, [*unknown* $width], [*unknown* $height])

...


