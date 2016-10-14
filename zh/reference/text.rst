文本助手（Text Helper）
========================

Phalcon中提供了 :code:`Phalcon\Text` 文本助手类，让你更简单地处理文本。

转为驼峰格式（Camelize）
------------------------

.. code-block:: php

    <?php

    echo Phalcon\Text::camelize('coco_bongo'); //CocoBongo



取消驼峰格式（Uncamelize）
--------------------------

.. code-block:: php

    <?php

    echo Phalcon\Text::uncamelize('CocoBongo'); //coco_bongo



增量（Increment）
-----------------
在字符串结尾追加数字，并进行累加。

.. code-block:: php

    <?php

    echo Phalcon\Text::increment("a"); // "a_1"
    echo Phalcon\Text::increment("a_1"); // "a_2"

