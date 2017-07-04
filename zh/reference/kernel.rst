内核类（Kernel Class）
======================


Message
-------
存在文件 messages/validation.php`，内容如下：

``` code-block:: php

    <?php

    return array(
        'Alnum' => '字段 :field 只能包含字母和数字',
        'Digit' => ':field 必须是数字',
    );

使用示例：

.. code-block:: php

    <?php

    Phalcon\Kernel::setBasePath("unit-tests/");
    echo Phalcon\Kernel::message('validation', 'Alnum'); // "字段 :field 只能包含字母和数字"

Alias
-----
存在文件 `alias/files.php`，内容如下：

``` code-block:: php

    <?php

    return array(
        '@app' => '/var/www/html/app',
        '@module' => '/var/www/html/module',
        '@public' => '/var/www/html/public',
    );

使用示例：

``` code-block:: php

    <?php

    Phalcon\Kernel::setBasePath("unit-tests/");
    echo Phalcon\Kernel::alias('files', '@app/config'); // "/var/www/html/app/config"
