使用模型（Working with Models）
===============================

模型代表了应用程序中的信息（数据）和处理数据的规则。模型主要用于管理与相应数据库表进行交互的规则。
大多数情况中，在应用程序中，数据库中每个表将对应一个模型。
应用程序中的大部分业务逻辑都将集中在模型里。

:doc:`Phalcon\\Mvc\\Model <../api/Phalcon_Mvc_Model>` 是 Phalcon 应用程序中所有模型的基类。它保证了数据库的独立性，基本的 CURD 操作，
高级的查询功能，多表关联等功能。
:doc:`Phalcon\\Mvc\\Model <../api/Phalcon_Mvc_Model>` 不需要直接使用 SQL 语句，因为它的转换方法，会动态的调用相应的数据库引擎进行处理。

.. highlights::

    模型是数据库的高级抽象层。如果您想进行低层次的数据库操作，您可以查看
    :doc:`Phalcon\\Db <../api/Phalcon_Db>` 组件文档。

创建模型（Creating Models）
---------------------------
模型是一个继承自 :doc:`Phalcon\\Mvc\\Model <../api/Phalcon_Mvc_Model>` 的一个类。 它必须放到 models 文件夹。一个模型文件必须包含一个类，
同时它的类名必须符合驼峰命名法：

.. code-block:: php

    <?php

    use Phalcon\Mvc\Model;

    class Robots extends Model
    {

    }

上面的例子显示了 "Robots" 模型的实现。 需要注意的是 Robots 继承自 :doc:`Phalcon\\Mvc\\Model <../api/Phalcon_Mvc_Model>` 。
因此，Robots 模型拥有了大量继承自该组件功能，包括基本的数据库 CRUD (Create, Read, Update, Delete) 操作，数据验证以及复杂的搜索支持，并且可以同时关联多个模型。

默认情况下，模型 "Robots" 对应的是数据库表 "robots"， 如果想映射到其他数据库表，可以使用 :code:`getSource()` 方法：

.. code-block:: php

    <?php

    use Phalcon\Mvc\Model;

    class Robots extends Model
    {
        public function getSource()
        {
            return "the_robots";
        }
    }

模型 Robots 现在映射到了 "the_robots" 表。:code:`initialize()` 方法可以帮助在模型中建立自定义行为，例如指定不同的数据库表。
:code:`initialize()` 方法在请求期间只被调用一次。

.. code-block:: php

    <?php

    use Phalcon\Mvc\Model;

    class Robots extends Model
    {
        public function initialize()
        {
            $this->setSource("the_robots");
        }
    }

:code:`initialize()` 方法在请求期间仅会被调用一次，目的是为应用中所有该模型的实例进行初始化。如果需要为每一个实例在创建的时候单独进行初始化，
可以使用 'onConstruct' 事件：

.. code-block:: php

    <?php

    use Phalcon\Mvc\Model;

    class Robots extends Model
    {
        public function onConstruct()
        {
            // ...
        }
    }

公共属性对比设置与取值 Setters/Getters（Public properties vs. Setters/Getters）
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
模型可以通过公共属性的方式实现，意味着模型的所有属性在实例化该模型的地方可以无限制的读取和更新。

.. code-block:: php

    <?php

    use Phalcon\Mvc\Model;

    class Robots extends Model
    {
        public $id;

        public $name;

        public $price;
    }

通过使用 getters/setters 方法，可以控制哪些属性可以公开访问，并且对属性值执行不同的形式的转换，同时可以保存在模型中的数据添加相应的验证规则。

.. code-block:: php

    <?php

    use Phalcon\Mvc\Model;

    class Robots extends Model
    {
        protected $id;

        protected $name;

        protected $price;

        public function getId()
        {
            return $this->id;
        }

        public function setName($name)
        {
            // The name is too short?
            if (strlen($name) < 10) {
                throw new \InvalidArgumentException('The name is too short');
            }
            $this->name = $name;
        }

        public function getName()
        {
            return $this->name;
        }

        public function setPrice($price)
        {
            // Negative prices aren't allowed
            if ($price < 0) {
                throw new \InvalidArgumentException('Price can\'t be negative');
            }
            $this->price = $price;
        }

        public function getPrice()
        {
            // Convert the value to double before be used
            return (double) $this->price;
        }
    }


公共属性的方式可以在开发中降低复杂度。而 getters/setters 的实现方式可以显著的增强应用的可测试性、扩展性和可维护性。
开发人员可以自己决定哪一种策略更加适合自己开发的应用。ORM同时兼容这两种方法。


模型放入命名空间（Models in Namespaces）
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
命名空间可以用来避免类名的冲突。ORM通过类名来映射相应的表名。比如 'Robots'：

.. code-block:: php

    <?php

    namespace Store\Toys;

    use Phalcon\Mvc\Model;

    class Robots extends Model
    {
        // ...
    }

Namespaces make part of model names when they are within strings:

.. code-block:: php

    <?php

    namespace Store\Toys;

    use Phalcon\Mvc\Model;

    class Robots extends Model
    {
        public $id;

        public $name;

        public function initialize()
        {
            $this->hasMany('id', 'Store\Toys\RobotsParts', 'robots_id');
        }
    }

理解记录对象（Understanding Records To Objects）
------------------------------------------------
每个模型的实例对应一条数据表中的记录。可以方便的通过读取对象的属性来访问相应的数据。比如，
一个表 "robots" 有如下数据：

.. code-block:: bash

    mysql> select * from robots;
    +----+------------+------------+------+
    | id | name       | type       | year |
    +----+------------+------------+------+
    |  1 | Robotina   | mechanical | 1972 |
    |  2 | Astro Boy  | mechanical | 1952 |
    |  3 | Terminator | cyborg     | 2029 |
    +----+------------+------------+------+
    3 rows in set (0.00 sec)

你可以通过主键找到某一条记录并且打印它的名称：

.. code-block:: php

    <?php

    // Find record with id = 3
    $robot = Robots::findFirst(3);

    // Prints "Terminator"
    echo $robot->name;

一旦记录被加载到内存中之后，你可以修改它的数据并保存所做的修改：

.. code-block:: php

    <?php

    $robot       = Robots::findFirst(3);
    $robot->name = "RoboCop";
    $robot->save();

如上所示，不需要写任何SQL语句。:doc:`Phalcon\\Mvc\\Model <../api/Phalcon_Mvc_Model>` 为web应用提供了高层数据库抽象。

查找记录（Finding Records）
---------------------------
:doc:`Phalcon\\Mvc\\Model <../api/Phalcon_Mvc_Model>` 为数据查询提供了多种方法。下面的例子将演示如何从一个模型中查找一条或者多条记录：

.. code-block:: php

    <?php

    // How many robots are there?
    $robots = Robots::find();
    echo "There are ", count($robots), "\n";

    // How many mechanical robots are there?
    $robots = Robots::find("type = 'mechanical'");
    echo "There are ", count($robots), "\n";

    // Get and print virtual robots ordered by name
    $robots = Robots::find(
        array(
            "type = 'virtual'",
            "order" => "name"
        )
    );
    foreach ($robots as $robot) {
        echo $robot->name, "\n";
    }

    // Get first 100 virtual robots ordered by name
    $robots = Robots::find(
        array(
            "type = 'virtual'",
            "order" => "name",
            "limit" => 100
        )
    );
    foreach ($robots as $robot) {
       echo $robot->name, "\n";
    }

.. highlights::

    如果需要通过外部数据（比如用户输入）或变量来查询记录，则必须要用`Binding Parameters`（绑定参数）的方式来防止SQL注入.

你可以使用 :code:`findFirst()` 方法获取第一条符合查询条件的结果：

.. code-block:: php

    <?php

    // What's the first robot in robots table?
    $robot = Robots::findFirst();
    echo "The robot name is ", $robot->name, "\n";

    // What's the first mechanical robot in robots table?
    $robot = Robots::findFirst("type = 'mechanical'");
    echo "The first mechanical robot name is ", $robot->name, "\n";

    // Get first virtual robot ordered by name
    $robot = Robots::findFirst(
        array(
            "type = 'virtual'",
            "order" => "name"
        )
    );
    echo "The first virtual robot name is ", $robot->name, "\n";

:code:`find()` 和 :code:`findFirst()` 方法都接受关联数组作为查询条件：

.. code-block:: php

    <?php

    $robot = Robots::findFirst(
        array(
            "type = 'virtual'",
            "order" => "name DESC",
            "limit" => 30
        )
    );

    $robots = Robots::find(
        array(
            "conditions" => "type = ?1",
            "bind"       => array(1 => "virtual")
        )
    );

可用的查询选项如下：

+-------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+
| 参数        | 描述                                                                                                                                                                                               | 举例                                                                            |
+=============+====================================================================================================================================================================================================+=================================================================================+
| conditions  | 查询操作的搜索条件。用于提取只有那些满足指定条件的记录。默认情况下 :doc:`Phalcon\\Mvc\\Model <../api/Phalcon_Mvc_Model>` 假定第一个参数就是查询条件。                                              | :code:`"conditions" => "name LIKE 'steve%'"`                                    |
+-------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+
| columns     | 只返回指定的字段，而不是模型所有的字段。 当用这个选项时，返回的是一个不完整的对象。                                                                                                                | :code:`"columns" => "id, name"`                                                 |
+-------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+
| bind        | 绑定与选项一起使用，通过替换占位符以及转义字段值从而增加安全性。                                                                                                                                   | :code:`"bind" => array("status" => "A", "type" => "some-time")`                 |
+-------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+
| bindTypes   | 当绑定参数时，可以使用这个参数为绑定参数定义额外的类型限制从而更加增强安全性。                                                                                                                     | :code:`"bindTypes" => array(Column::BIND_PARAM_STR, Column::BIND_PARAM_INT)`    |
+-------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+
| order       | 用于结果排序。使用一个或者多个字段，逗号分隔。                                                                                                                                                     | :code:`"order" => "name DESC, status"`                                          |
+-------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+
| limit       | 限制查询结果的数量在一定范围内。                                                                                                                                                                   | :code:`"limit" => 10`                                                           |
+-------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+
| offset      | Offset the results of the query by a certain amount                                                                                                                                                | :code:`"offset" => 5`                                                           |
+-------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+
| group       | 从多条记录中获取数据并且根据一个或多个字段对结果进行分组。                                                                                                                                         | :code:`"group" => "name, status"`                                               |
+-------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+
| for_update  | 通过这个选项， :doc:`Phalcon\\Mvc\\Model <../api/Phalcon_Mvc_Model>`  读取最新的可用数据，并且为读到的每条记录设置独占锁。                                                                         | :code:`"for_update" => true`                                                    |
+-------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+
| shared_lock | 通过这个选项， :doc:`Phalcon\\Mvc\\Model <../api/Phalcon_Mvc_Model>`  读取最新的可用数据，并且为读到的每条记录设置共享锁。                                                                         | :code:`"shared_lock" => true`                                                   |
+-------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+
| cache       | 缓存结果集，减少了连续访问数据库。                                                                                                                                                                 | :code:`"cache" => array("lifetime" => 3600, "key" => "my-find-key")`            |
+-------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+
| hydration   | Sets the hydration strategy to represent each returned record in the result                                                                                                                        | :code:`"hydration" => Resultset::HYDRATE_OBJECTS`                               |
+-------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+

如果你愿意，除了使用数组作为查询参数外，还可以通过一种面向对象的方式来创建查询：

.. code-block:: php

    <?php

    $robots = Robots::query()
        ->where("type = :type:")
        ->andWhere("year < 2000")
        ->bind(array("type" => "mechanical"))
        ->order("name")
        ->execute();

静态方法 :code:`query()` 返回一个对IDE自动完成友好的 :doc:`Phalcon\\Mvc\\Model\\Criteria <../api/Phalcon_Mvc_Model_Criteria>`  对象。

所有查询在内部都以 :doc:`PHQL <phql>` 查询的方式处理。PHQL是一个高层的、面向对象的类SQL语言。通过PHQL语言你可以使用更多的比如join其他模型、定义分组、添加聚集等特性。

最后，还有一个 :code:`findFirstBy<property-name>()` 方法。这个方法扩展了前面提及的 :code:`findFirst()` 方法。它允许您利用方法名中的属性名称，通过将要搜索的该字段的内容作为参数传给它，来快速从一个表执行检索操作。

还是用上面用过的 Robots 模型来举例说明：

.. code-block:: php

    <?php

    use Phalcon\Mvc\Model;

    class Robots extends Model
    {
        public $id;

        public $name;

        public $price;
    }

我们这里有3个属性：:code:`$id`, :code:`$name` 和 :code:`$price`。因此，我们以想要查询第一个名称为 'Terminator' 的记录为例，可以这样写：

.. code-block:: php

    <?php

    $name  = "Terminator";
    $robot = Robots::findFirstByName($name);

    if ($robot) {
        $this->flash->success("The first robot with the name " . $name . " cost " . $robot->price ".");
    } else {
        $this->flash->error("There were no robots found in our table with the name " . $name ".");
    }

请注意我们在方法调用中用的是 'Name'，并向它传递了变量 :code:`$name`， :code:`$name` 的值就是我们想要找的记录的名称。另外注意，当我们的查询找到了符合的记录后，这个记录的其他属性也都是可用的。

模型结果集（Model Resultsets）
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
:code:`findFirst()` 方法直接返回一个被调用对象的实例（如果有结果返回的话），而 :code:`find()` 方法返回一个 :doc:`Phalcon\\Mvc\\Model\\Resultset\\Simple <../api/Phalcon_Mvc_Model_Resultset_Simple>` 对象。这个对象也封装进了所有结果集的功能，比如遍历、查找特定的记录、统计等等。

这些对象比一般数组功能更强大。最大的特点是 :doc:`Phalcon\\Mvc\\Model\\Resultset <../api/Phalcon_Mvc_Model_Resultset>` 每时每刻只有一个结果在内存中。这对操作大数据量时的内存管理相当有帮助。

.. code-block:: php

    <?php

    // Get all robots
    $robots = Robots::find();

    // Traversing with a foreach
    foreach ($robots as $robot) {
        echo $robot->name, "\n";
    }

    // Traversing with a while
    $robots->rewind();
    while ($robots->valid()) {
        $robot = $robots->current();
        echo $robot->name, "\n";
        $robots->next();
    }

    // Count the resultset
    echo count($robots);

    // Alternative way to count the resultset
    echo $robots->count();

    // Move the internal cursor to the third robot
    $robots->seek(2);
    $robot = $robots->current();

    // Access a robot by its position in the resultset
    $robot = $robots[5];

    // Check if there is a record in certain position
    if (isset($robots[3])) {
       $robot = $robots[3];
    }

    // Get the first record in the resultset
    $robot = $robots->getFirst();

    // Get the last record
    $robot = $robots->getLast();

Phalcon 的结果集模拟了可滚动的游标，你可以通过位置，或者内部指针去访问任何一条特定的记录。注意有一些数据库系统不支持滚动游标，这就使得查询会被重复执行，
以便回放光标到最开始的位置，然后获得相应的记录。类似地，如果多次遍历结果集，那么必须执行相同的查询次数。

将大数据量的查询结果存储在内存会消耗很多资源，正因为如此，分成每32行一块从数据库中获得结果集，以减少重复执行查询请求的次数，在一些情况下也节省内存。

注意结果集可以序列化后保存在一个后端缓存里面。 :doc:`Phalcon\\Cache <cache>` 可以用来实现这个。但是，序列化数据会导致 :doc:`Phalcon\\Mvc\\Model <../api/Phalcon_Mvc_Model>`
将从数据库检索到的所有数据以一个数组的方式保存，因此在这样执行的地方会消耗更多的内存。

.. code-block:: php

    <?php

    // Query all records from model parts
    $parts = Parts::find();

    // Store the resultset into a file
    file_put_contents("cache.txt", serialize($parts));

    // Get parts from file
    $parts = unserialize(file_get_contents("cache.txt"));

    // Traverse the parts
    foreach ($parts as $part) {
        echo $part->id;
    }

过滤结果集（Filtering Resultsets）
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
过滤数据最有效的方法是设置一些查询条件，数据库会利用表的索引快速返回数据。Phalcon 额外的允许你通过任何数据库不支持的方式过滤数据。

.. code-block:: php

    <?php

    $customers = Customers::find()->filter(
        function ($customer) {

            // Return only customers with a valid e-mail
            if (filter_var($customer->email, FILTER_VALIDATE_EMAIL)) {
                return $customer;
            }
        }
    );

将结果集转为数组（Resultsets Convert To Array）
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code-block:: php

    <?php

    $customers = Customers::find();
    $arr = $customers->toArray();

    $columns = array('id', 'name'); // 需要输出的字段
    $rename = true; // 字段名是否是映射后的名称
    $negate = false;
    $arr = $customers->toArray($columns, $rename, $negate);

绑定参数（Binding Parameters）
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
在 :doc:`Phalcon\\Mvc\\Model <../api/Phalcon_Mvc_Model>` 中也支持绑定参数。即使使用绑定参数对性能有一点很小的影响，还是强烈建议您使用这种方法，以消除代码受SQL注入攻击的可能性。
绑定参数支持字符串和整数占位符。实现方法如下：

.. code-block:: php

    <?php

    // Query robots binding parameters with string placeholders
    $conditions = "name = :name: AND type = :type:";

    // Parameters whose keys are the same as placeholders
    $parameters = array(
        "name" => "Robotina",
        "type" => "maid"
    );

    // Perform the query
    $robots = Robots::find(
        array(
            $conditions,
            "bind" => $parameters
        )
    );

    // Query robots binding parameters with integer placeholders
    $conditions = "name = ?1 AND type = ?2";
    $parameters = array(1 => "Robotina", 2 => "maid");
    $robots     = Robots::find(
        array(
            $conditions,
            "bind" => $parameters
        )
    );

    // Query robots binding parameters with both string and integer placeholders
    $conditions = "name = :name: AND type = ?1";

    // Parameters whose keys are the same as placeholders
    $parameters = array(
        "name" => "Robotina",
        1      => "maid"
    );

    // Perform the query
    $robots = Robots::find(
        array(
            $conditions,
            "bind" => $parameters
        )
    );

When using numeric placeholders, you will need to define them as integers i.e. 1 or 2. In this case "1" or "2" are considered strings
and not numbers, so the placeholder could not be successfully replaced.

Strings are automatically escaped using PDO_. This function takes into account the connection charset, so its recommended to define
the correct charset in the connection parameters or in the database configuration, as a wrong charset will produce undesired effects
when storing or retrieving data.

Additionally you can set the parameter "bindTypes", this allows defining how the parameters should be bound according to its data type:

.. code-block:: php

    <?php

    use Phalcon\Db\Column;

    // Bind parameters
    $parameters = array(
        "name" => "Robotina",
        "year" => 2008
    );

    // Casting Types
    $types = array(
        "name" => Column::BIND_PARAM_STR,
        "year" => Column::BIND_PARAM_INT
    );

    // Query robots binding parameters with string placeholders
    $robots = Robots::find(
        array(
            "name = :name: AND year = :year:",
            "bind"      => $parameters,
            "bindTypes" => $types
        )
    );

.. highlights::

    Since the default bind-type is :code:`Phalcon\Db\Column::BIND_PARAM_STR`, there is no need to specify the
    "bindTypes" parameter if all of the columns are of that type.

If you bind arrays in bound parameters, keep in mind, that keys must be numbered from zero:

.. code-block:: php

    <?php

    $array = ["a","b","c"]; // $array: [[0] => "a", [1] => "b", [2] => "c"]

    unset($array[1]); // $array: [[0] => "a", [2] => "c"]

    // Now we have to renumber the keys
    $array = array_values($array); // $array: [[0] => "a", [1] => "c"]

    $robots = Robots::find(
        array(
            'letter IN ({letter:array})',
            'bind' => array(
                'letter' => $array
            )
        )
    );

.. highlights::

    Bound parameters are available for all query methods such as :code:`find()` and :code:`findFirst()` but also the calculation
    methods like :code:`count()`, :code:`sum()`, :code:`average()` etc.

If you're using "finders", bound parameters are automatically used for you:

.. code-block:: php

    <?php

    // Explicit query using bound parameters
    $robots = Robots::find(
        array(
            "name = ?0",
            "bind" => ["Ultron"],
        )
    );

    // Implicit query using bound parameters
    $robots = Robots::findByName("Ultron");

获取记录的初始化以及准备（Initializing/Preparing fetched records）
------------------------------------------------------------------
May be the case that after obtaining a record from the database is necessary to initialise the data before
being used by the rest of the application. You can implement the method 'afterFetch' in a model, this event
will be executed just after create the instance and assign the data to it:

.. code-block:: php

    <?php

    use Phalcon\Mvc\Model;

    class Robots extends Model
    {
        public $id;

        public $name;

        public $status;

        public function beforeSave()
        {
            // Convert the array into a string
            $this->status = join(',', $this->status);
        }

        public function afterFetch()
        {
            // Convert the string to an array
            $this->status = explode(',', $this->status);
        }

        public function afterSave()
        {
            // Convert the string to an array
            $this->status = explode(',', $this->status);
        }

        public function afterToArray($arr)
        {
            unset($arr['status']);
        }
    }

If you use getters/setters instead of/or together with public properties, you can initialize the field once it is
accessed:

.. code-block:: php

    <?php

    use Phalcon\Mvc\Model;

    class Robots extends Model
    {
        public $id;

        public $name;

        public $status;

        public function getStatus()
        {
            return explode(',', $this->status);
        }
    }

聚合运算（Generating Calculations）
-----------------------------------
模型类 :doc:`Phalcon\\Mvc\\Model <../api/Phalcon_Mvc_Model>` 提供的聚合运算方法，使用的是数据库内置函数计算结果，例如：COUNT, SUM, MAX, MIN or AVG。

累计（Count）
^^^^^^^^^^^^^

.. code-block:: php

    <?php

    // How many employees are?
    $rowcount = Employees::count();

    // How many different areas are assigned to employees?
    $rowcount = Employees::count(
        array(
            "distinct" => "area"
        )
    );

    // How many employees are in the Testing area?
    $rowcount = Employees::count(
        "area = 'Testing'"
    );

    // Count employees grouping results by their area
    $group = Employees::count(
        array(
            "group" => "area"
        )
    );
    foreach ($group as $row) {
       echo "There are ", $row->rowcount, " in ", $row->area;
    }

    // Count employees grouping by their area and ordering the result by count
    $group = Employees::count(
        array(
            "group" => "area",
            "order" => "rowcount"
        )
    );

    // Avoid SQL injections using bound parameters
    $group = Employees::count(
        array(
            "type > ?0",
            "bind" => array($type)
        )
    );

累加（Sum）
^^^^^^^^^^^

.. code-block:: php

    <?php

    // How much are the salaries of all employees?
    $total = Employees::sum(
        array(
            "column" => "salary"
        )
    );

    // How much are the salaries of all employees in the Sales area?
    $total = Employees::sum(
        array(
            "column"     => "salary",
            "conditions" => "area = 'Sales'"
        )
    );

    // Generate a grouping of the salaries of each area
    $group = Employees::sum(
        array(
            "column" => "salary",
            "group"  => "area"
        )
    );
    foreach ($group as $row) {
       echo "The sum of salaries of the ", $row->area, " is ", $row->sumatory;
    }

    // Generate a grouping of the salaries of each area ordering
    // salaries from higher to lower
    $group = Employees::sum(
        array(
            "column" => "salary",
            "group"  => "area",
            "order"  => "sumatory DESC"
        )
    );

    // Avoid SQL injections using bound parameters
    $group = Employees::sum(
        array(
            "conditions" => "area > ?0",
            "bind"       => array($area)
        )
    );

平均（Average）
^^^^^^^^^^^^^^^

.. code-block:: php

    <?php

    // What is the average salary for all employees?
    $average = Employees::average(
        array(
            "column" => "salary"
        )
    );

    // What is the average salary for the Sales's area employees?
    $average = Employees::average(
        array(
            "column"     => "salary",
            "conditions" => "area = 'Sales'"
        )
    );

    // Avoid SQL injections using bound parameters
    $average = Employees::average(
        array(
            "column"     => "age",
            "conditions" => "area > ?0",
            "bind"       => array($area)
        )
    );

最大/最小（Max/Min）
^^^^^^^^^^^^^^^^^^^^

.. code-block:: php

    <?php

    // What is the oldest age of all employees?
    $age = Employees::maximum(
        array(
            "column" => "age"
        )
    );

    // What is the oldest of employees from the Sales area?
    $age = Employees::maximum(
        array(
            "column"     => "age",
            "conditions" => "area = 'Sales'"
        )
    );

    // What is the lowest salary of all employees?
    $salary = Employees::minimum(
        array(
            "column" => "salary"
        )
    );


创建与更新结果判断（Create/Update with Confidence）
---------------------------------------------------
当我们使用 :code:`Phalcon\Mvc\Model::save()` 保存数据时，可能是创建或者更新了一条数据。如果我们想确保使用创建或更新操作，需要使用 :code:`create()` 或 :code:`update()`：

.. code-block:: php

    <?php

    $robot       = new Robots();
    $robot->type = "mechanical";
    $robot->name = "Astro Boy";
    $robot->year = 1952;

    // This record only must be created
    if ($robot->create() == false) {
        echo "Umh, We can't store robots right now: \n";
        foreach ($robot->getMessages() as $message) {
            echo $message, "\n";
        }
    } else {
        echo "Great, a new robot was created successfully!";
    }

可以通过向方法 :code:`Phalcon\Mvc\Model::create()`、:code:`Phalcon\Mvc\Model::update()` 以及  and :code:`Phalcon\Mvc\Model::save()` 传递数组来进行复制，我们也可以通过方法 :code:`Phalcon\Mvc\Model::assign()` 进行赋值。

验证信息（Validation Messages）
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
模型 :doc:`Phalcon\\Mvc\\Model <../api/Phalcon_Mvc_Model>` 拥有有一个灵活的消息子系统，当插入或者更新数据发生错误时，会生成验证消息，通过 :code:`getMessages()` 方法返回。
每条验证信息都是类 :doc:`Phalcon\\Validation\\Message <../api/Phalcon_Validation_Message>` 的实例，包含了字段名、验证消息、类型等信息：

.. code-block:: php

    <?php

    if ($robot->save() == false) {
        foreach ($robot->getMessages() as $message) {
            echo "Message: ", $message->getMessage();
            echo "Field: ", $message->getField();
            echo "Type: ", $message->getType();
        }
    }

:doc:`Phalcon\\Mvc\\Model <../api/Phalcon_Mvc_Model>` 默认情况下会根据字段类型以及数据库操作结果生成下列验证信息：

+----------------------+------------------------------------------------------------------------------------------------------------------------------------+
| Type                 | Description                                                                                                                        |
+======================+====================================================================================================================================+
| PresenceOf           | Generated when a field with a non-null attribute on the database is trying to insert/update a null value                           |
+----------------------+------------------------------------------------------------------------------------------------------------------------------------+
| ConstraintViolation  | Generated when a field part of a virtual foreign key is trying to insert/update a value that doesn't exist in the referenced model |
+----------------------+------------------------------------------------------------------------------------------------------------------------------------+
| InvalidValue         | Generated when a validator failed because of an invalid value                                                                      |
+----------------------+------------------------------------------------------------------------------------------------------------------------------------+
| InvalidCreateAttempt | Produced when a record is attempted to be created but it already exists                                                            |
+----------------------+------------------------------------------------------------------------------------------------------------------------------------+
| InvalidUpdateAttempt | Produced when a record is attempted to be updated but it doesn't exist                                                             |
+----------------------+------------------------------------------------------------------------------------------------------------------------------------+

更多的模型验证相关的内容查看 :doc:`模型验证 <models-validation>` 章节。

模型事件与事件管理器（Events and Events Manager）
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
模型允许我们定义事件的回调方法，通过它们帮助我们实现自己的业务逻辑。以下是模型 :doc:`Phalcon\\Mvc\\Model <../api/Phalcon_Mvc_Model>` 支持的事件和它们的执行顺序：

+--------------------+--------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------+
| Operation          | Name                     | Can stop operation?   | Explanation                                                                                                                       |
+====================+==========================+=======================+===================================================================================================================================+
| Inserting/Updating | beforeValidation         | YES                   | Is executed before the fields are validated for not nulls/empty strings or foreign keys                                           |
+--------------------+--------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------+
| Inserting          | beforeValidationOnCreate | YES                   | Is executed before the fields are validated for not nulls/empty strings or foreign keys when an insertion operation is being made |
+--------------------+--------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------+
| Updating           | beforeValidationOnUpdate | YES                   | Is executed before the fields are validated for not nulls/empty strings or foreign keys when an updating operation is being made  |
+--------------------+--------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------+
| Inserting/Updating | onValidationFails        | YES (already stopped) | Is executed after an integrity validator fails                                                                                    |
+--------------------+--------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------+
| Inserting          | afterValidationOnCreate  | YES                   | Is executed after the fields are validated for not nulls/empty strings or foreign keys when an insertion operation is being made  |
+--------------------+--------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------+
| Updating           | afterValidationOnUpdate  | YES                   | Is executed after the fields are validated for not nulls/empty strings or foreign keys when an updating operation is being made   |
+--------------------+--------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------+
| Inserting/Updating | afterValidation          | YES                   | Is executed after the fields are validated for not nulls/empty strings or foreign keys                                            |
+--------------------+--------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------+
| Inserting/Updating | beforeSave               | YES                   | Runs before the required operation over the database system                                                                       |
+--------------------+--------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------+
| Updating           | beforeUpdate             | YES                   | Runs before the required operation over the database system only when an updating operation is being made                         |
+--------------------+--------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------+
| Inserting          | beforeCreate             | YES                   | Runs before the required operation over the database system only when an inserting operation is being made                        |
+--------------------+--------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------+
| Updating           | afterUpdate              | NO                    | Runs after the required operation over the database system only when an updating operation is being made                          |
+--------------------+--------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------+
| Inserting          | afterCreate              | NO                    | Runs after the required operation over the database system only when an inserting operation is being made                         |
+--------------------+--------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------+
| Inserting/Updating | afterSave                | NO                    | Runs after the required operation over the database system                                                                        |
+--------------------+--------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------+

模型中自定义事件（Implementing Events in the Model's class）
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
The easier way to make a model react to events is implement a method with the same name of the event in the model's class:

.. code-block:: php

    <?php

    use Phalcon\Mvc\Model;

    class Robots extends Model
    {
        public function beforeValidationOnCreate()
        {
            echo "This is executed before creating a Robot!";
        }
    }

Events can be useful to assign values before performing an operation, for example:

.. code-block:: php

    <?php

    use Phalcon\Mvc\Model;

    class Products extends Model
    {
        public function beforeCreate()
        {
            // Set the creation date
            $this->created_at = date('Y-m-d H:i:s');
        }

        public function beforeUpdate()
        {
            // Set the modification date
            $this->modified_in = date('Y-m-d H:i:s');
        }
    }

使用自定义事件管理器（Using a custom Events Manager）
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Additionally, this component is integrated with :doc:`Phalcon\\Events\\Manager <../api/Phalcon_Events_Manager>`,
this means we can create listeners that run when an event is triggered.

.. code-block:: php

    <?php

    use Phalcon\Mvc\Model;
    use Phalcon\Events\Manager as EventsManager;

    class Robots extends Model
    {
        public function initialize()
        {
            $eventsManager = new EventsManager();

            // Attach an anonymous function as a listener for "model" events
            $eventsManager->attach('model', function ($event, $robot) {
                if ($event->getType() == 'beforeSave') {
                    if ($robot->name == 'Scooby Doo') {
                        echo "Scooby Doo isn't a robot!";
                        return false;
                    }
                }

                return true;
            });

            // Attach the events manager to the event
            $this->setEventsManager($eventsManager);
        }
    }

In the example given above, the Events Manager only acts as a bridge between an object and a listener (the anonymous function).
Events will be fired to the listener when 'robots' are saved:

.. code-block:: php

    <?php

    $robot       = new Robots();
    $robot->name = 'Scooby Doo';
    $robot->year = 1969;

    $robot->save();

If we want all objects created in our application use the same EventsManager, then we need to assign it to the Models Manager:

.. code-block:: php

    <?php

    // Registering the modelsManager service
    $di->setShared('modelsManager', function () {

        $eventsManager = new \Phalcon\Events\Manager();

        // Attach an anonymous function as a listener for "model" events
        $eventsManager->attach('model', function ($event, $model) {

            // Catch events produced by the Robots model
            if (get_class($model) == 'Robots') {

                if ($event->getType() == 'beforeSave') {
                    if ($model->name == 'Scooby Doo') {
                        echo "Scooby Doo isn't a robot!";
                        return false;
                    }
                }
            }

            return true;
        });

        // Setting a default EventsManager
        $modelsManager = new ModelsManager();
        $modelsManager->setEventsManager($eventsManager);

        return $modelsManager;
    });

If a listener returns false that will stop the operation that is executing currently.

实现业务逻辑（Implementing a Business Rule）
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
When an insert, update or delete is executed, the model verifies if there are any methods with the names of
the events listed in the table above.

We recommend that validation methods are declared protected to prevent that business logic implementation
from being exposed publicly.

The following example implements an event that validates the year cannot be smaller than 0 on update or insert:

.. code-block:: php

    <?php

    use Phalcon\Mvc\Model;

    class Robots extends Model
    {
        public function beforeSave()
        {
            if ($this->year < 0) {
                echo "Year cannot be smaller than zero!";
                return false;
            }
        }
    }

Some events return false as an indication to stop the current operation. If an event doesn't return anything, :doc:`Phalcon\\Mvc\\Model <../api/Phalcon_Mvc_Model>`
will assume a true value.



防止 SQL 注入（Avoiding SQL injections）
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Every value assigned to a model attribute is escaped depending of its data type. A developer doesn't need to escape manually
each value before storing it on the database. Phalcon uses internally the `bound parameters <http://php.net/manual/en/pdostatement.bindparam.php>`_
capability provided by PDO to automatically escape every value to be stored in the database.

.. code-block:: bash

    mysql> desc products;
    +------------------+------------------+------+-----+---------+----------------+
    | Field            | Type             | Null | Key | Default | Extra          |
    +------------------+------------------+------+-----+---------+----------------+
    | id               | int(10) unsigned | NO   | PRI | NULL    | auto_increment |
    | product_types_id | int(10) unsigned | NO   | MUL | NULL    |                |
    | name             | varchar(70)      | NO   |     | NULL    |                |
    | price            | decimal(16,2)    | NO   |     | NULL    |                |
    | active           | char(1)          | YES  |     | NULL    |                |
    +------------------+------------------+------+-----+---------+----------------+
    5 rows in set (0.00 sec)

If we use just PDO to store a record in a secure way, we need to write the following code:

.. code-block:: php

    <?php

    $name           = 'Artichoke';
    $price          = 10.5;
    $active         = 'Y';
    $productTypesId = 1;

    $sql = 'INSERT INTO products VALUES (null, :productTypesId, :name, :price, :active)';
    $sth = $dbh->prepare($sql);

    $sth->bindParam(':productTypesId', $productTypesId, PDO::PARAM_INT);
    $sth->bindParam(':name', $name, PDO::PARAM_STR, 70);
    $sth->bindParam(':price', doubleval($price));
    $sth->bindParam(':active', $active, PDO::PARAM_STR, 1);

    $sth->execute();

The good news is that Phalcon do this for you automatically:

.. code-block:: php

    <?php

    $product                   = new Products();
    $product->product_types_id = 1;
    $product->name             = 'Artichoke';
    $product->price            = 10.5;
    $product->active           = 'Y';

    $product->create();

删除记录（Deleting Records）
----------------------------
The method :code:`Phalcon\Mvc\Model::delete()` allows to delete a record. You can use it as follows:

.. code-block:: php

    <?php

    $robot = Robots::findFirst(11);

    if ($robot != false) {
        if ($robot->delete() == false) {
            echo "Sorry, we can't delete the robot right now: \n";

            foreach ($robot->getMessages() as $message) {
                echo $message, "\n";
            }
        } else {
            echo "The robot was deleted successfully!";
        }
    }

You can also delete many records by traversing a resultset with a foreach:

.. code-block:: php

    <?php

    foreach (Robots::find("type='mechanical'") as $robot) {
        if ($robot->delete() == false) {
            echo "Sorry, we can't delete the robot right now: \n";

            foreach ($robot->getMessages() as $message) {
                echo $message, "\n";
            }
        } else {
            echo "The robot was deleted successfully!";
        }
    }

The following events are available to define custom business rules that can be executed when a delete operation is
performed:

+-----------+--------------+---------------------+------------------------------------------+
| Operation | Name         | Can stop operation? | Explanation                              |
+===========+==============+=====================+==========================================+
| Deleting  | beforeDelete | YES                 | Runs before the delete operation is made |
+-----------+--------------+---------------------+------------------------------------------+
| Deleting  | afterDelete  | NO                  | Runs after the delete operation was made |
+-----------+--------------+---------------------+------------------------------------------+

With the above events can also define business rules in the models:

.. code-block:: php

    <?php

    use Phalcon\Mvc\Model;

    class Robots extends Model
    {
        public function beforeDelete()
        {
            if ($this->status == 'A') {
                echo "The robot is active, it can't be deleted";

                return false;
            }

            return true;
        }
    }

动态更新（Use Dynamic Update）
------------------------------
设置了动态更新，模型将会自动根据查询快照，去判断是否有字段值发生了更改，如果有更改才会去保存更新：

.. code-block:: php

    <?php

    use Phalcon\Mvc\Model;

    class Robots extends Model
    {
        public function initialize()
        {
            $this->useDynamicUpdate(true);
        }
    }

获取发生变化的字段列表：

.. code-block:: php

    <?php

    // Get a record from the database
    $robot = Robots::findFirst();

    // Change a column
    $robot->name = 'Other name';

    var_dump($robot->getChangedFields()); // ['name']
    var_dump($robot->hasChanged('name')); // true
    var_dump($robot->hasChanged('type')); // false

设置模式（Pointing to a different schema）
------------------------------------------
If a model is mapped to a table that is in a different schemas/databases than the default. You can use the getSchema method to define that:

如果一个模型映射到一个在非默认的schemas/数据库中的表，你可以通过 getSchema 方法去定义它：

.. code-block:: php

    <?php

    use Phalcon\Mvc\Model;

    class Robots extends Model
    {
        public function getSchema()
        {
            return "toys";
        }
    }

记录底层 SQL 语句（Logging Low-Level SQL Statements）
-----------------------------------------------------
When using high-level abstraction components such as :doc:`Phalcon\\Mvc\\Model <../api/Phalcon_Mvc_Model>` to access a database, it is
difficult to understand which statements are finally sent to the database system. :doc:`Phalcon\\Mvc\\Model <../api/Phalcon_Mvc_Model>`
is supported internally by :doc:`Phalcon\\Db <../api/Phalcon_Db>`. :doc:`Phalcon\\Logger <../api/Phalcon_Logger>` interacts
with :doc:`Phalcon\\Db <../api/Phalcon_Db>`, providing logging capabilities on the database abstraction layer, thus allowing us to log SQL
statements as they happen.

.. code-block:: php

    <?php

    use Phalcon\Logger;
    use Phalcon\Events\Manager;
    use Phalcon\Logger\Adapter\File as FileLogger;
    use Phalcon\Db\Adapter\Pdo\Mysql as Connection;

    $di->set('db', function () {

        $eventsManager = new EventsManager();

        $logger = new FileLogger("app/logs/debug.log");

        // Listen all the database events
        $eventsManager->attach('db', function ($event, $connection) use ($logger) {
            if ($event->getType() == 'beforeQuery') {
                $logger->log($connection->getSQLStatement(), Logger::INFO);
            }
        });

        $connection = new Connection(
            array(
                "host"     => "localhost",
                "username" => "root",
                "password" => "secret",
                "dbname"   => "invo"
            )
        );

        // Assign the eventsManager to the db adapter instance
        $connection->setEventsManager($eventsManager);

        return $connection;
    });

As models access the default database connection, all SQL statements that are sent to the database system will be logged in the file:

.. code-block:: php

    <?php

    $robot             = new Robots();
    $robot->name       = "Robby the Robot";
    $robot->created_at = "1956-07-21";

    if ($robot->save() == false) {
        echo "Cannot save robot";
    }

As above, the file *app/logs/db.log* will contain something like this:

.. code-block:: irc

    [Mon, 30 Apr 12 13:47:18 -0500][DEBUG][Resource Id #77] INSERT INTO robots
    (name, created_at) VALUES ('Robby the Robot', '1956-07-21')

分析 SQL 语句（Profiling SQL Statements）
-----------------------------------------
Thanks to :doc:`Phalcon\\Db <../api/Phalcon_Db>`, the underlying component of :doc:`Phalcon\\Mvc\\Model <../api/Phalcon_Mvc_Model>`,
it's possible to profile the SQL statements generated by the ORM in order to analyze the performance of database operations. With
this you can diagnose performance problems and to discover bottlenecks.

.. code-block:: php

    <?php

    use Phalcon\Db\Profiler as ProfilerDb;
    use Phalcon\Events\Manager as EventsManager;
    use Phalcon\Db\Adapter\Pdo\Mysql as MysqlPdo;

    $di->set('profiler', function () {
        return new ProfilerDb();
    }, true);

    $di->set('db', function () use ($di) {

        $eventsManager = new EventsManager();

        // Get a shared instance of the DbProfiler
        $profiler      = $di->getProfiler();

        // Listen all the database events
        $eventsManager->attach('db', function ($event, $connection) use ($profiler) {
            if ($event->getType() == 'beforeQuery') {
                $profiler->startProfile($connection->getSQLStatement());
            }

            if ($event->getType() == 'afterQuery') {
                $profiler->stopProfile();
            }
        });

        $connection = new MysqlPdo(
            array(
                "host"     => "localhost",
                "username" => "root",
                "password" => "secret",
                "dbname"   => "invo"
            )
        );

        // Assign the eventsManager to the db adapter instance
        $connection->setEventsManager($eventsManager);

        return $connection;
    });

Profiling some queries:

.. code-block:: php

    <?php

    // Send some SQL statements to the database
    Robots::find();
    Robots::find(
        array(
            "order" => "name"
        )
    );
    Robots::find(
        array(
            "limit" => 30
        )
    );

    // Get the generated profiles from the profiler
    $profiles = $di->get('profiler')->getProfiles();

    foreach ($profiles as $profile) {
       echo "SQL Statement: ", $profile->getSQLStatement(), "\n";
       echo "Start Time: ", $profile->getInitialTime(), "\n";
       echo "Final Time: ", $profile->getFinalTime(), "\n";
       echo "Total Elapsed Time: ", $profile->getTotalElapsedSeconds(), "\n";
    }

Each generated profile contains the duration in milliseconds that each instruction takes to complete as well as the generated SQL statement.

元数据（Meta-Data）
-------------------
在这里将介绍如何获取模型在数据库中对应表的元数据。

自定义元数据（Manual Meta-Data）
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
在模型中添加 :code:`metaData` 方法即可。 :doc:`了解更多 <models-metadata>`

自定义字段（Manual Fields）
^^^^^^^^^^^^^^^^^^^^^^^^^^^
有时候我们只是想简单的隐藏一些字段，在模型中覆盖 :code:`getAttributes` 方法即可，实现代码如下：

.. code-block:: php

    <?php

    // Create a model
    class Robots extends Model
    {
        public function getAttributes()
        {
            return array('id', 'name');
        }
    }

获取字段真实名称（Gets Real Field）
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
实现代码如下：

.. code-block:: php

    <?php


    use Phalcon\Mvc\Model;

    class Robots extends Model
    {
        public function columnMap()
        {
            // Keys are the real names in the table and
            // the values their names in the application
            return array(
                'id'       => 'code',
                'the_name' => 'theName',
                'the_type' => 'theType',
                'the_year' => 'theYear'
            );
        }
    }

    $robot = new Robots;
    echo $robot->getRealAttribute('code');


.. _PDO: http://www.php.net/manual/en/pdo.prepared-statements.php
.. _date: http://php.net/manual/en/function.date.php
.. _time: http://php.net/manual/en/function.time.php
.. _Traits: http://php.net/manual/en/language.oop5.traits.php
