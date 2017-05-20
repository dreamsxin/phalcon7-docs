数组助手（Array Helper）
========================

Phalcon中提供了 :code:`Phalcon\Arr` 数组助手类，让你更高效地处理数组。

获取值（Gets Value）
--------------------

.. code-block:: php

    <?php

	$_GET['id'] = array(1, 2);
	$_GET['name'] = array('phalcon', 'phalcon7');

    $value = \Phalcon\Arr::get($_GET, 'name'); // 值为数组 array('phalcon', 'phalcon7')
    $value = \Phalcon\Arr::first($_GET, 'name'); // 值为 phalcon
    $value = \Phalcon\Arr::path($_GET, array('id', 'name')); // 值为 array('id' => array(1, 2), 'name' => array('phalcon', 'phalcon7'))

方法的第一个参数是我们从哪里获取值，第二个参数指定了如何获取数据，第三个参数指定了如果不存在值的情况下返回的默认值。第二个参数可以是下述几种类型中的一个：

- 数组键名或者欲从中取值的对象的属性名称
- 数组键名或对象的属性名称数组
- 回调函数

用原生PHP从一个对象、数组、或者包含这两者的一个复杂数据结构中获取数据是非常繁琐的。你首先得使用isset 检查 key 是否存在, 然后如果存在你就获取它，如果不存在，则提供一个默认返回值，Phalcon 提供了一个非常方便的方法来做这件事：

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

    $value = \Phalcon\Arr::get($data, 'sex', '男');

通过路径获取值（Gets Value）
----------------------------

.. code-block:: php

    <?php

    $value = \Phalcon\Arr::path($_GET, 'foo.bar.name');

方法的第一个参数是我们从哪里获取值，第二个参数指定了如何获取数据，第三个参数指定了如果不存在值的情况下返回的默认值，第四个参数指定了键名用什么分隔符，第二个参数可以是下述几种类型中的一个：

- 数组键名
- 以分隔符分割的数组键名，可以使用通配符（*）
- 数组键名数组

对象转换为数组（Converts an object into an array）
--------------------------------------------------
你经常要将一个对象或者对象的数组转换成一个数组，如下代码可完成这个工作：

.. code-block:: php

    <?php

    $arr = \Phalcon\Arr::toArray($object);

    $properties = array('id', 'name'); // 需要输出的字段
    $recursive = true; // 是否递归获取，如果属性是对象或者数组
    $negate = false;
    $arr = \Phalcon\Arr::toArray($object, $colums, $rename, $negate);

下面的例子中展示了基本的使用方法：

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
