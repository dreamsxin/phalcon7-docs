数组助手（Array Helper）
========================

Phalcon中提供了 :code:`Phalcon\Arr` 数组助手类，让你更高效地处理数组。。

获取值（Gets Value）
--------------------

.. code-block:: php

    <?php

    $value = \Phalcon\Arr::get($_GET);
    $value = \Phalcon\Arr::path($_GET, 'foo.bar.name');

用原生PHP从一个对象、数组、或者包含这两者的一个复杂数据结构中获取数据是非常繁琐的。你首先得使用isset 检查 key 是否存在, 然后如果存在你就获取它，如果不存在，则提供一个默认返回值，下面的例子中展示了基本的使用方法：

.. code-block:: php

    <?php

    $data = array(
        'username' => 'Dreamszhu',
        'password' => '123456',
        'address' => 'ZheJiang',
        'foo' => array('bar' => 'Hello World'),
        'theme' => array(
            'one' => array('color' => 'green'),
            'two' => array('color' => 'red', 'size' => 11)
        )
    );

    \Phalcon\Arr::is_assoc($data);

    // 判断是否是数组
    \Phalcon\Arr::is_array($data);
    
    // Get the value of $data['foo']['bar']
    $value = \Phalcon\Arr::path($data, 'foo.bar');

    $colors = \Phalcon\Arr::path($data, 'theme.*.color');

    // Using an array of keys
    $colors = \Phalcon\Arr::path($data, array('theme', '*', 'color'));

    // Set the values of "color" in theme
    \Phalcon\Arr::set_path($data, 'theme.*.color', 'blue');
    $colors = \Phalcon\Arr::path($data, array('theme', '*', 'color'));

    // Append the values of "color" in theme
    \Phalcon\Arr::set_path($data, 'theme.*.color', 'red', NULL, true);
    $colors = \Phalcon\Arr::path($data, array('theme', '*', 'color'));

    $values = \Phalcon\Arr::range(5, 20);

    // Get the value "username", if it exists
    $username = \Phalcon\Arr::get($data, 'username');

    $sex = \Phalcon\Arr::get($data, 'sex', 'No');

    $info = \Phalcon\Arr::get($data, array('username', 'address'));

    $sex = \Phalcon\Arr::choice($data, 'sex', 'one', 'two');

    // Get the values "username", "password"
    $auth = \Phalcon\Arr::extract($data, array('username', 'password'));

    $data = array(
        array('id' => 1, 'name' => 'Google'),
        array('id' => 2, 'name' => 'Baidu')
    );

    // Get all of the "id" values from a result
    $ids = \Phalcon\Arr::pluck($data, 'id');
