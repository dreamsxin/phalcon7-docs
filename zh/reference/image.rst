图像处理（Image manipulation）
==============================
图像组件给应用提供图像缩放、截取、翻转、反射等功能。

图像驱动适配器（Image Driver Adapters）
---------------------------------------
Phalcon 内置下列驱动适配器：

+------------+---------------------------------------------------------------------------------------+
| 名称       | API                                                                                   |
+============+=======================================================================================+
| GD         | :doc:`Phalcon\\Image\\Adapter\\GD <../api/Phalcon_Image_Adapter_GD>`                  |
+------------+---------------------------------------------------------------------------------------+
| Imagick    | :doc:`Phalcon\\Image\\Adapter\\Imagick <../api/Phalcon_Image_Adapter_Imagick>`        |
+------------+---------------------------------------------------------------------------------------+

图像另存（Image Save）
----------------------
示例：

.. code-block:: php

    <?php

    $image = new Phalcon\Image\Adapter\GD('unit-tests/assets/phalconphp.jpg');
    // 另存
    $image->save('unit-tests/assets/production/gd-resize.jpg');

方法 :code`save` 的第一个参数是指定保存路径，如果为空，将覆盖原始文件，第二个参数指定图像质量 [1-100] 之间。

图像渲染（Image Render）
------------------------
示例：

.. code-block:: php

    <?php

    $image = new Phalcon\Image\Adapter\GD('unit-tests/assets/phalconphp.jpg');
    // 获取二进制字符串
    $bytes = $image->render();
    $this->response->setContentType('image/png');
    $this->response->setContent($bytes);
    $this->response->send();

图像缩放（Image Resize）
------------------------
示例：

.. code-block:: php

    <?php

    $image = new Phalcon\Image\Adapter\GD('unit-tests/assets/phalconphp.jpg');
    // 缩放
    $image->resize(200, 200);

方法 :code`resize` 的第一个参数是指定宽度，第二个参数指定高度，第三个参数指定了缩放方式，默认为 `Phalcon\Image::AUTO`。第三个参数有以下几个值：

- Phalcon\Image::AUTO     设置了该值，将计算原始宽度和设定宽度比 与 原始高度和设定高度比的值大小，值大的选择按设置的宽度等比缩放。
- Phalcon\Image::INVERSE  设置了该值，将计算原始宽度和设定宽度比 与 原始高度和设定高度比的值大小，值大的选择按设置的高度等比缩放。
- Phalcon\Image::WIDTH    设置了该值，必须设置宽度，将根据设置的宽度等比缩放图像
- Phalcon\Image::HEIGHT   设置了该值，必须设置高度，将根据设置的高度等比缩放图像
- Phalcon\Image::PRECISE  设置了该值，将计算设置宽高比 与 原始宽高比 的值大小，值大的选择按设置的高度等比缩放。
- Phalcon\Image::NONE     设置了该值，允许拉伸，将使用设定的宽度和高度进行缩放，宽度或高度允许为空，将使用原始图像宽度或高度。
- Phalcon\Image::TENSILE  设置了该值，允许拉伸，将使用设定的宽度和高度进行缩放。
- Phalcon\Image::NARROW   设置了该值，如果设置的宽度或高度超出图像原始尺寸，将自动使用原始尺寸替换。

图像添加水印（Add Watermark To Image）
--------------------------------------
可以添加水印到指定位置，示例：

.. code-block:: php

    <?php

    $mask = new Phalcon\Image\Adapter\GD('watermark.jpg');
    $image->watermark($watermark, -10, -10, 90);

图像添加文本（Add Text To Image）
---------------------------------
可以添加文本到指定位置，下面的示例将会添加文本到图像正中间位置：

.. code-block:: php

    <?php

    $image->text('Hello world');

图像添加倒影（Add Reflection To Image）
--------------------------------------
可以添加指定高度的倒影，示例：

.. code-block:: php

    <?php

    $image->reflection(20, 90);

图像遮罩（Image Mask）
----------------------
示例：

.. code-block:: php

    <?php

    $mask = new Phalcon\Image\Adapter\GD('mask.jpg');
    $image->mask($mask);

方法 :code`background`  参数必须是图像对象。

图像设置背景色（Image Background）
----------------------------------
示例：

.. code-block:: php

    <?php

    $image->background('#000000', 90);

方法 :code`background` 的第一个参数是指定背景颜色值，默认值为 `000000`，第二个参数指定透明度，范围 [1-100]。

图像高斯模糊（Blur Image）
--------------------------
示例：

.. code-block:: php

    <?php

    $image->blur(10);

方法 :code`blur` 参数默认值为 1，范围 [1-100]。


图像像素化（Pixelate Image）
----------------------------
示例：

.. code-block:: php

    <?php

    $image->pixelate(15);

方法 :code`pixelate` 参数默认值为 10。

.. _GD: http://php.net/manual/en/book.image.php
.. _ImageMagick: http://php.net/manual/en/book.imagick.php
