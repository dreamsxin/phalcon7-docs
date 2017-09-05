图形库（Chart）
===============
提供常用的图形生成类。

图形生成类（Chart Class）
-------------------------
Phalcon 内置下列图形生成类：

+-------------+------------------------------------------------------------------------------+
| 名称        | API                                                                          |
+=============+==============================================================================+
| QRcode      | :doc:`Phalcon\\Chart\\QRcode <../api/Phalcon_Chart_QRcode>`                  |
+-------------+------------------------------------------------------------------------------+
| Captcha     | :doc:`Phalcon\\Chart\\Captcha <../api/Phalcon_Chart_Captcha>`                |
+-------------+------------------------------------------------------------------------------+
| TinyCaptcha | :doc:`Phalcon\\Chart\\Captcha\\Tiny <../api/Phalcon_Chart_Captcha_Tiny>      |
+-------------+------------------------------------------------------------------------------+

二维码生成（QRcode Generate）
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
示例：

.. code-block:: php

    <?php

    $qr = new Phalcon\Chart\QRcode();
    $bytes = $qr->render();

验证码（Captcha Generate）
^^^^^^^^^^^^^^^^^^^^^^^^^^
示例：

.. code-block:: php

    <?php

    $code = Phalcon\Text::random(Phalcon\Text::RANDOM_ALNUM, 4);
    $captcha = new Phalcon\Chart\Captcha($code);
    $bytes = $captcha->render();

