Class **Phalcon\\Image\\Adapter\\Imagick**
==========================================

*extends* abstract class :doc:`Phalcon\\Image\\Adapter <Phalcon_Image_Adapter>`

*implements* :doc:`Phalcon\\Image\\AdapterInterface <Phalcon_Image_AdapterInterface>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/image/adapter/imagick.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Image manipulation support. Allows images to be resized, cropped, etc.  

.. code-block:: php

    <?php

    $image = new Phalcon\Image\Adapter\Imagick("upload/test.jpg");
    $image->resize(200, 200)->rotate(90)->crop(100, 100);
    if ($image->save()) {
    	echo 'success';
    }



Methods
-------

public static *boolean*  **check** ()

Checks if Imagick is enabled



public  **__construct** (*string* $file, [*unknown* $width], [*unknown* $height])

Phalcon\\Image\\Imagick constructor



protected  **_resize** (*int* $width, *int* $height)

Execute a resize.



protected  **_liquidRescale** (*unknown* $width, *unknown* $height, *unknown* $delta_x, *unknown* $regidity)

This method scales the images using liquid rescaling method. Only support Imagick



protected  **_crop** (*int* $width, *int* $height, *int* $offset_x, *int* $offset_y)

Execute a crop.



protected  **_rotate** (*int* $degrees)

Execute a rotation.



protected  **_flip** (*int* $direction)

Execute a flip.



protected  **_sharpen** (*int* $amount)

Execute a sharpen.



protected  **_reflection** (*int* $height, *int* $opacity, *boolean* $fade_in)

Execute a reflection.



protected  **_watermark** (:doc:`Phalcon\\Image\\Adapter <Phalcon_Image_Adapter>` $watermark, *int* $offset_x, *int* $offset_y, *int* $opacity)

Execute a watermarking.



protected  **_text** (*string* $text, *int* $offset_x, *int* $offset_y, *int* $opacity, *int* $r, *int* $g, *int* $b, *int* $size, *string* $fontfile)

Execute a text



protected  **_mask** (*unknown* $mask)

Composite one image onto another



protected  **_background** (*int* $r, *int* $g, *int* $b, *int* $opacity)

Execute a background.



protected  **_blur** (*unknown* $radius)

Blur image



protected  **_pixelate** (*unknown* $amount)

Pixelate image



protected *boolean*  **_save** (*string* $file, *int* $quality)

Execute a save.



protected *string*  **_render** (*string* $type, *int* $quality)

Execute a render.



public  **__destruct** ()

Destroys the loaded image to free up resources.



public :doc:`Phalcon\\Image\\Adapter\\Imagick <Phalcon_Image_Adapter_Imagick>`  **line** (*int* $sx, *int* $sy, *int* $ex, *int* $ey, [*string* $color])

Draws a line



public :doc:`Phalcon\\Image\\Adapter\\Imagick <Phalcon_Image_Adapter_Imagick>`  **polygon** (*array* $coordinates, [*string* $color])

Draws a polygon 

.. code-block:: php

    <?php

     $coordinates = array( array( 'x' => 4, 'y' => 6 ), array( 'x' => 8, 'y' => 10 ) );
     $image->polygon($coordinates);




public  **shadow** ([*unknown* $color], [*unknown* $opacity], [*unknown* $sigma], [*unknown* $x], [*unknown* $y])

...


public  **getInternalImInstance** ()

...


public static  **setResourceLimit** (*unknown* $resource, *unknown* $limit)

...


public :doc:`Phalcon\\Image\\Adapter\\Imagick <Phalcon_Image_Adapter_Imagick>`  **colorize** (*unknown* $color, [*unknown* $composition])

Replicate Colorize function



public :doc:`Phalcon\\Image\\Adapter\\Imagick <Phalcon_Image_Adapter_Imagick>`  **gamma** (*unknown* $gamma, [*unknown* $channel])

Change the gamma of an image



public :doc:`Phalcon\\Image\\Adapter\\Imagick <Phalcon_Image_Adapter_Imagick>`  **levels** ([*float* $gamma], [*unknown* $input_min], [*unknown* $input_max], [*unknown* $output_min], [*unknown* $output_max], [*unknown* $channel])

Replicate Photoshop's levels function



public :doc:`Phalcon\\Image\\Adapter\\Imagick <Phalcon_Image_Adapter_Imagick>`  **brightness_contrast** (*unknown* $brightness, *unknown* $contrast)

Replicate brightness/contrast photoshop function Now this one is a bit of a pain. PHP's extension doesn't provide us with this handle (yet?) So we have to save the image to disk at this point, perform the function using the command line, and reload the image. yay.



public :doc:`Phalcon\\Image\\Adapter\\Imagick <Phalcon_Image_Adapter_Imagick>`  **hsl** ([*unknown* $hue], [*unknown* $saturation], [*unknown* $lightness])

Replicate HSL function Imagemagick calls this 'modulate



public :doc:`Phalcon\\Image\\Adapter\\Imagick <Phalcon_Image_Adapter_Imagick>`  **curves_graph** (*unknown* $fx)

Perform an imagemagick-style function on each pixel



public :doc:`Phalcon\\Image\\Adapter\\Imagick <Phalcon_Image_Adapter_Imagick>`  **vignette** (*unknown* $color, [*unknown* $composition], [*unknown* $crop_factor])

Adds a vignette to the image



public :doc:`Phalcon\\Image\\Adapter\\Imagick <Phalcon_Image_Adapter_Imagick>`  **earlybird** ()

A sort-of sepia filter



public :doc:`Phalcon\\Image\\Adapter\\Imagick <Phalcon_Image_Adapter_Imagick>`  **inkwell** ()

A black and white filter



public static  **convert** (*unknown* $command)

...


public *string*  **getRealPath** () inherited from Phalcon\\Image\\Adapter

Returns the real path of the image file



public *int*  **getWidth** () inherited from Phalcon\\Image\\Adapter

Returns the width of images



public *int*  **getHeight** () inherited from Phalcon\\Image\\Adapter

Returns the height of images



public *int*  **getType** () inherited from Phalcon\\Image\\Adapter

Returns the type of images



public *string*  **getMime** () inherited from Phalcon\\Image\\Adapter

Returns the mime of images



public *resource*  **getImage** () inherited from Phalcon\\Image\\Adapter

Returns the image of images



public :doc:`Phalcon\\Image\\Adapter <Phalcon_Image_Adapter>`  **resize** ([*unknown* $width], [*unknown* $height], [*unknown* $master]) inherited from Phalcon\\Image\\Adapter

Resize the image to the given size. Either the width or the height can be omitted and the image will be resized proportionally.



public :doc:`Phalcon\\Image\\Adapter <Phalcon_Image_Adapter>`  **liquidRescale** (*unknown* $width, *unknown* $height, [*unknown* $delta_x], [*unknown* $rigidity]) inherited from Phalcon\\Image\\Adapter

This method scales the images using liquid rescaling method. Only support Imagick



public :doc:`Phalcon\\Image\\Adapter <Phalcon_Image_Adapter>`  **crop** (*unknown* $width, *unknown* $height, [*unknown* $offset_x], [*unknown* $offset_y]) inherited from Phalcon\\Image\\Adapter

Crop an image to the given size. Either the width or the height can be omitted and the current width or height will be used.



public :doc:`Phalcon\\Image\\Adapter <Phalcon_Image_Adapter>`  **rotate** (*unknown* $degrees) inherited from Phalcon\\Image\\Adapter

Rotate the image by a given amount.



public :doc:`Phalcon\\Image\\Adapter <Phalcon_Image_Adapter>`  **flip** (*unknown* $direction) inherited from Phalcon\\Image\\Adapter

Flip the image along the horizontal or vertical axis.



public :doc:`Phalcon\\Image\\Adapter <Phalcon_Image_Adapter>`  **sharpen** (*unknown* $amount) inherited from Phalcon\\Image\\Adapter

Sharpen the image by a given amount.



public :doc:`Phalcon\\Image\\Adapter <Phalcon_Image_Adapter>`  **reflection** ([*unknown* $height], [*unknown* $opacity], [*unknown* $fade_in]) inherited from Phalcon\\Image\\Adapter

Add a reflection to an image. The most opaque part of the reflection will be equal to the opacity setting and fade out to full transparent. Alpha transparency is preserved.



public :doc:`Phalcon\\Image\\AdapterInterface <Phalcon_Image_AdapterInterface>`  **watermark** (*unknown* $watermark, [*unknown* $offset_x], [*unknown* $offset_y], [*unknown* $opacity]) inherited from Phalcon\\Image\\Adapter

Add a watermark to an image with a specified opacity. Alpha transparency will be preserved.



public :doc:`Phalcon\\Image\\Adapter <Phalcon_Image_Adapter>`  **text** (*string* $text, [*unknown* $offset_x], [*unknown* $offset_y], [*unknown* $opacity], [*unknown* $color], [*unknown* $size], [*unknown* $fontfile]) inherited from Phalcon\\Image\\Adapter

Add a text to an image with a specified opacity.



public :doc:`Phalcon\\Image\\Adapter <Phalcon_Image_Adapter>`  **mask** (*unknown* $mask) inherited from Phalcon\\Image\\Adapter

Composite one image onto another



public :doc:`Phalcon\\Image\\Adapter <Phalcon_Image_Adapter>`  **background** (*unknown* $color, [*unknown* $opacity]) inherited from Phalcon\\Image\\Adapter

Set the background color of an image. This is only useful for images with alpha transparency.



public :doc:`Phalcon\\Image\\Adapter <Phalcon_Image_Adapter>`  **blur** ([*unknown* $radius]) inherited from Phalcon\\Image\\Adapter

Blur image



public :doc:`Phalcon\\Image\\Adapter <Phalcon_Image_Adapter>`  **pixelate** ([*unknown* $amount]) inherited from Phalcon\\Image\\Adapter

Pixelate image



public *boolean*  **save** ([*unknown* $file], [*unknown* $opacity]) inherited from Phalcon\\Image\\Adapter

Save the image. If the filename is omitted, the original image will be overwritten.



public *string*  **render** ([*unknown* $type], [*unknown* $opacity]) inherited from Phalcon\\Image\\Adapter

Render the image and return the binary string.



public *string*  **getColorRBG** (*unknown* $color) inherited from Phalcon\\Image\\Adapter

Render the image and return the binary string.



