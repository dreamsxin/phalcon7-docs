模型的高级用法（Working with Models (Advanced)）
================================================

结果集结合模式（Hydration Modes）
---------------------------------
模型的结果集是模型对象的集合，这意味着每个返回的结果是一个对象对应数据库中的一行数据。这些对象可以被修改并保存：

.. code-block:: php

    <?php

    // Manipulating a resultset of complete objects
    foreach (Robots::find() as $robot) {
        $robot->year = 2000;
        $robot->save();
    }

当我们想将结果只用于只读时，我们可以通过设置结合模式为数组或者 `stdClass`，我们将这种策略叫做 'hydration mode'：

.. code-block:: php

    <?php

    use Phalcon\Mvc\Model\Resultset;

    $robots = Robots::find();

    // Return every robot as an array
    $robots->setHydrateMode(Resultset::HYDRATE_ARRAYS);

    foreach ($robots as $robot) {
        echo $robot['year'], PHP_EOL;
    }

    // Return every robot as a stdClass
    $robots->setHydrateMode(Resultset::HYDRATE_OBJECTS);

    foreach ($robots as $robot) {
        echo $robot->year, PHP_EOL;
    }

    // Return every robot as a Robots instance
    $robots->setHydrateMode(Resultset::HYDRATE_RECORDS);

    foreach ($robots as $robot) {
        echo $robot->year, PHP_EOL;
    }

我们可以在方法 `find` 中传递结合模式：

.. code-block:: php

    <?php

    use Phalcon\Mvc\Model\Resultset;

    $robots = Robots::find(
        array(
            'hydration' => Resultset::HYDRATE_ARRAYS
        )
    );

    foreach ($robots as $robot) {
        echo $robot['year'], PHP_EOL;
    }

创建与更新记录（Creating Updating/Records）
-------------------------------------------
Phalcon\\Mvc\\Model::save() 方法允许你创建/更新记录。save方法自动调用 :doc:`Phalcon\\Mvc\\Model <../api/Phalcon_Mvc_Model>` 内部的create和update方法，
如果想达到预期般的工作效果，正确定义实体主键是非常必须的，以确保创建和更新记录成功。

Also the method executes associated validators, virtual foreign keys and events that are defined in the model:

.. code-block:: php

    <?php

    $robot       = new Robots();
    $robot->type = "mechanical";
    $robot->name = "Astro Boy";
    $robot->year = 1952;

    if ($robot->save() == false) {
        echo "Umh, We can't store robots right now: \n";
        foreach ($robot->getMessages() as $message) {
            echo $message, "\n";
        }
    } else {
        echo "Great, a new robot was saved successfully!";
    }

An array could be passed to "save" to avoid assign every column manually. :doc:`Phalcon\\Mvc\\Model <../api/Phalcon_Mvc_Model>` will check if there are setters implemented for
the columns passed in the array giving priority to them instead of assign directly the values of the attributes:

.. code-block:: php

    <?php

    $robot = new Robots();

    $robot->save(
        array(
            "type" => "mechanical",
            "name" => "Astro Boy",
            "year" => 1952
        )
    );

Values assigned directly or via the array of attributes are escaped/sanitized according to the related attribute data type. So you can pass
an insecure array without worrying about possible SQL injections:

.. code-block:: php

    <?php

    $robot = new Robots();
    $robot->save($_POST);

.. highlights::

    Without precautions mass assignment could allow attackers to set any database column's value. Only use this feature
    if you want to permit a user to insert/update every column in the model, even if those fields are not in the submitted
    form.

You can set an additional parameter in 'save' to set a whitelist of fields that only must taken into account when doing
the mass assignment:

.. code-block:: php

    <?php

    $robot = new Robots();

    $robot->save(
        $_POST,
        array(
            'name',
            'type'
        )
    );

自动生成标识列（Auto-generated identity columns）
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Some models may have identity columns. These columns usually are the primary key of the mapped table. :doc:`Phalcon\\Mvc\\Model <../api/Phalcon_Mvc_Model>`
can recognize the identity column omitting it in the generated SQL INSERT, so the database system can generate an auto-generated value for it.
Always after creating a record, the identity field will be registered with the value generated in the database system for it:

.. code-block:: php

    <?php

    $robot->save();

    echo "The generated id is: ", $robot->id;

:doc:`Phalcon\\Mvc\\Model <../api/Phalcon_Mvc_Model>` is able to recognize the identity column. Depending on the database system, those columns may be
serial columns like in PostgreSQL or auto_increment columns in the case of MySQL.

PostgreSQL uses sequences to generate auto-numeric values, by default, Phalcon tries to obtain the generated value from the sequence "table_field_seq",
for example: robots_id_seq, if that sequence has a different name, the method "getSequenceName" needs to be implemented:

.. code-block:: php

    <?php

    use Phalcon\Mvc\Model;

    class Robots extends Model
    {
        public function getSequenceName()
        {
            return "robots_sequence_name";
        }
    }

忽略指定列的数据（Skipping Columns）
------------------------------------
To tell :doc:`Phalcon\\Mvc\\Model <../api/Phalcon_Mvc_Model>` that always omits some fields in the creation and/or update of records in order
to delegate the database system the assignation of the values by a trigger or a default:

.. code-block:: php

    <?php

    use Phalcon\Mvc\Model;

    class Robots extends Model
    {
        public function initialize()
        {
            // Skips fields/columns on both INSERT/UPDATE operations
            $this->skipAttributes(
                array(
                    'year',
                    'price'
                )
            );

            // Skips only when inserting
            $this->skipAttributesOnCreate(
                array(
                    'created_at'
                )
            );

            // Skips only when updating
            $this->skipAttributesOnUpdate(
                array(
                    'modified_in'
                )
            );
        }
    }

This will ignore globally these fields on each INSERT/UPDATE operation on the whole application.
If you want to ignore different attributes on different INSERT/UPDATE operations, you can specify the second parameter (boolean) - true
for replacement. Forcing a default value can be done in the following way:

.. code-block:: php

    <?php

    use Phalcon\Db\RawValue;

    $robot             = new Robots();
    $robot->name       = 'Bender';
    $robot->year       = 1999;
    $robot->created_at = new RawValue('default');

    $robot->create();

A callback also can be used to create a conditional assignment of automatic default values:

.. code-block:: php

    <?php

    use Phalcon\Mvc\Model;
    use Phalcon\Db\RawValue;

    class Robots extends Model
    {
        public function beforeCreate()
        {
            if ($this->price > 10000) {
                $this->type = new RawValue('default');
            }
        }
    }

.. highlights::

    Never use a :doc:`Phalcon\\Db\\RawValue <../api/Phalcon_Db_RawValue>` to assign external data (such as user input)
    or variable data. The value of these fields is ignored when binding parameters to the query.
    So it could be used to attack the application injecting SQL.

动态更新（Dynamic Update）
^^^^^^^^^^^^^^^^^^^^^^^^^^
SQL UPDATE statements are by default created with every column defined in the model (full all-field SQL update).
You can change specific models to make dynamic updates, in this case, just the fields that had changed
are used to create the final SQL statement.

In some cases this could improve the performance by reducing the traffic between the application and the database server,
this specially helps when the table has blob/text fields:

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

独立的列映射（Independent Column Mapping）
------------------------------------------
The ORM supports an independent column map, which allows the developer to use different column names in the model to the ones in
the table. Phalcon will recognize the new column names and will rename them accordingly to match the respective columns in the database.
This is a great feature when one needs to rename fields in the database without having to worry about all the queries
in the code. A change in the column map in the model will take care of the rest. For example:

.. code-block:: php

    <?php

    namespace Store\Toys;

    use Phalcon\Mvc\Model;

    class Robots extends Model
    {
        public $code;

        public $theName;

        public $theType;

        public $theYear;

        public function columnMap()
        {
            // Keys are the real names in the table and
            // the values their names in the application
            return [
                "id"       => "code",
                "the_name" => "theName",
                "the_type" => "theType",
                "the_year" => "theYear",
            ];
        }
    }

Then you can use the new names naturally in your code:

.. code-block:: php

    <?php

    use Store\Toys\Robots;

    // Find a robot by its name
    $robot = Robots::findFirst(
        "theName = 'Voltron'"
    );

    echo $robot->theName, "\n";

    // Get robots ordered by type
    $robot = Robots::find(
        [
            "order" => "theType DESC",
        ]
    );

    foreach ($robots as $robot) {
        echo "Code: ", $robot->code, "\n";
    }

    // Create a robot
    $robot = new Robots();

    $robot->code    = "10101";
    $robot->theName = "Bender";
    $robot->theType = "Industrial";
    $robot->theYear = 2999;

    $robot->save();

Take into consideration the following the next when renaming your columns:

* References to attributes in relationships/validators must use the new names
* Refer the real column names will result in an exception by the ORM

The independent column map allow you to:

* Write applications using your own conventions
* Eliminate vendor prefixes/suffixes in your code
* Change column names without change your application code

记录快照（Record Snapshots）
----------------------------
Specific models could be set to maintain a record snapshot when they're queried. You can use this feature to implement auditing or just to know what
fields are changed according to the data queried from the persistence:

.. code-block:: php

    <?php

    namespace Store\Toys;

    use Phalcon\Mvc\Model;

    class Robots extends Model
    {
        public function initialize()
        {
            $this->keepSnapshots(true);
        }
    }

When activating this feature the application consumes a bit more of memory to keep track of the original values obtained from the persistence.
In models that have this feature activated you can check what fields changed:

.. code-block:: php

    <?php

    use Store\Toys\Robots;

    // Get a record from the database
    $robot = Robots::findFirst();

    // Change a column
    $robot->name = "Other name";

    var_dump($robot->getChangedFields()); // ["name"]

    var_dump($robot->hasChanged("name")); // true

    var_dump($robot->hasChanged("type")); // false

设置模式（Pointing to a different schema）
------------------------------------------
如果一个模型映射到一个在非默认的schemas/数据库中的表，你可以通过 :code:`setSchema()` 方法去定义它：

.. code-block:: php

    <?php

    namespace Store\Toys;

    use Phalcon\Mvc\Model;

    class Robots extends Model
    {
        public function initialize()
        {
            $this->setSchema("toys");
        }
    }

设置多个数据库（Setting multiple databases）
--------------------------------------------
In Phalcon, all models can belong to the same database connection or have an individual one. Actually, when
:doc:`Phalcon\\Mvc\\Model <../api/Phalcon_Mvc_Model>` needs to connect to the database it requests the "db" service
in the application's services container. You can overwrite this service setting it in the initialize method:

在Phalcon中，所有模型可以属于同一个数据库连接，也可以分属独立的数据库连接。实际上，当 :doc:`Phalcon\\Mvc\\Model <../api/Phalcon_Mvc_Model>`
需要连接数据库的时候，它在应用服务容器内请求"db"这个服务。 可以通过在 initialize 方法内重写这个服务的设置。

.. code-block:: php

    <?php

    use Phalcon\Db\Adapter\Pdo\Mysql as MysqlPdo;
    use Phalcon\Db\Adapter\Pdo\PostgreSQL as PostgreSQLPdo;

    // This service returns a MySQL database
    $di->set('dbMysql', function () {
        return new MysqlPdo(
            array(
                "host"     => "localhost",
                "username" => "root",
                "password" => "secret",
                "dbname"   => "invo"
            )
        );
    });

    // This service returns a PostgreSQL database
    $di->set('dbPostgres', function () {
        return new PostgreSQLPdo(
            array(
                "host"     => "localhost",
                "username" => "postgres",
                "password" => "",
                "dbname"   => "invo"
            )
        );
    });

Then, in the initialize method, we define the connection service for the model:

然后，在 Initialize 方法内，我们为这个模型定义数据库连接。

.. code-block:: php

    <?php

    use Phalcon\Mvc\Model;

    class Robots extends Model
    {
        public function initialize()
        {
            $this->setConnectionService('dbPostgres');
        }
    }

实现读写分离（Reading and Writing Separation）
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
But Phalcon offers you more flexibility, you can define the connection that must be used to 'read' and for 'write'. This is specially useful
to balance the load to your databases implementing a master-slave architecture:

另外Phalcon还提供了更多的灵活性，你可分别定义用来读取和写入的数据库连接。这对实现主从架构的数据库负载均衡非常有用。

.. code-block:: php

    <?php

    use Phalcon\Mvc\Model;

    class Robots extends Model
    {
        public function initialize()
        {
            $this->setReadConnectionService('dbSlave');
            $this->setWriteConnectionService('dbMaster');
        }
    }

也可以用如下方法实现：

.. code-block:: php

    <?php

    use Phalcon\Mvc\Model;

    class Robots extends Model
    {
        /**
         * 动态选择读数据库连接
         *
         * @param array $intermediate
         * @param array $bindParams
         * @param array $bindTypes
         */
        public function selectReadConnection($intermediate, $bindParams, $bindTypes)
        {
            return $this->getDI()->get('readDB');
        }

        /**
         * 动态选择写数据库连接
         *
         * @param array $intermediate
         * @param array $bindParams
         * @param array $bindTypes
         */
        public function selectWriteConnection($intermediate, $bindParams, $bindTypes)
        {
            return $this->getDI()->get('writeDB');
        }
    }

The ORM also provides Horizontal Sharding facilities, by allowing you to implement a 'shard' selection
according to the current query conditions:

另外ORM还可以通过根据当前查询条件来实现一个 'shared' 选择器，来实现水平切分的功能。

.. code-block:: php

    <?php

    use Phalcon\Mvc\Model;

    class Robots extends Model
    {
        /**
         * 动态选择读数据库连接
         *
         * @param array $intermediate
         * @param array $bindParams
         * @param array $bindTypes
         */
        public function selectReadConnection($intermediate, $bindParams, $bindTypes)
        {
            // Check if there is a 'where' clause in the select
            if (isset($intermediate['where'])) {

                $conditions = $intermediate['where'];

                // Choose the possible shard according to the conditions
                if ($conditions['left']['name'] == 'id') {
                    $id = $conditions['right']['value'];

                    if ($id > 0 && $id < 10000) {
                        return $this->getDI()->get('dbShard1');
                    }

                    if ($id > 10000) {
                        return $this->getDI()->get('dbShard2');
                    }
                }
            }

            // Use a default shard
            return $this->getDI()->get('dbShard0');
        }

        /**
         * 动态选择写数据库连接
         *
         * @param array $intermediate
         * @param array $bindParams
         * @param array $bindTypes
         */
        public function selectWriteConnection($intermediate, $bindParams, $bindTypes)
        {
            // Check if there is a 'where' clause in the select

            // Use a default shard
            return $this->getDI()->get('dbShard0');
        }
    }

The method 'selectReadConnection' is called to choose the right connection, this method intercepts any new
query executed:

'selectReadConnection' 方法用来选择正确的数据库连接，这个方法拦截任何新的查询操作：

.. code-block:: php

    <?php

    $robot = Robots::findFirst('id = 101');


.. highlights::

    在 :doc:`Model查询器 <phql>` 中可实现同样的功能。

注入服务到模型（Injecting services into Models）
------------------------------------------------
You may be required to access the application services within a model, the following example explains how to do that:

你可能需要在模型中用到应用中注入的服务，下面的例子会教你如何去做：

.. code-block:: php

    <?php

    use Phalcon\Mvc\Model;

    class Robots extends Model
    {
        public function notSaved()
        {
            // Obtain the flash service from the DI container
            $flash = $this->getDI()->getFlash();

            // Show validation messages
            foreach ($this->getMessages() as $message) {
                $flash->error($message);
            }
        }
    }

The "notSaved" event is triggered every time that a "create" or "update" action fails. So we're flashing the validation messages
obtaining the "flash" service from the DI container. By doing this, we don't have to print messages after each save.

每当 "create" 或者 "update" 操作失败时会触发 "notSave" 事件。所以我们从DI中获取 "flash" 服务并推送确认消息。这样的话，我们不需要每次在save之后去打印信息。

禁用或启用特性（Disabling/Enabling Features）
---------------------------------------------
In the ORM we have implemented a mechanism that allow you to enable/disable specific features or options globally on the fly.
According to how you use the ORM you can disable that you aren't using. These options can also be temporarily disabled if required:

.. code-block:: php

    <?php

    use Phalcon\Mvc\Model;

    Model::setup(
        array(
            'events'         => false,
            'columnRenaming' => false
        )
    );

The available options are:

+---------------------+---------------------------------------------------------------------------------------+---------+
| Option              | Description                                                                           | Default |
+=====================+=======================================================================================+=========+
| events              | Enables/Disables callbacks, hooks and event notifications from all the models         | true    |
+---------------------+---------------------------------------------------------------------------------------+---------+
| columnRenaming      | Enables/Disables the column renaming                                                  | true    |
+---------------------+---------------------------------------------------------------------------------------+---------+
| notNullValidations  | The ORM automatically validate the not null columns present in the mapped table       | true    |
+---------------------+---------------------------------------------------------------------------------------+---------+
| virtualForeignKeys  | Enables/Disables the virtual foreign keys                                             | true    |
+---------------------+---------------------------------------------------------------------------------------+---------+
| phqlLiterals        | Enables/Disables literals in the PHQL parser                                          | true    |
+---------------------+---------------------------------------------------------------------------------------+---------+
| lateStateBinding    | Enables/Disables late state binding of the method :code:`Mvc\Model::cloneResultMap()` | false   |
+---------------------+---------------------------------------------------------------------------------------+---------+

独立的组件（Stand-Alone component）
-----------------------------------
Using :doc:`Phalcon\\Mvc\\Model <models>` in a stand-alone mode can be demonstrated below:

.. code-block:: php

    <?php

    use Phalcon\Di;
    use Phalcon\Mvc\Model;
    use Phalcon\Mvc\Model\Manager as ModelsManager;
    use Phalcon\Db\Adapter\Pdo\Sqlite as Connection;
    use Phalcon\Mvc\Model\Metadata\Memory as MetaData;

    $di = new Di();

    // Setup a connection
    $di->set(
        'db',
        new Connection(
            array(
                "dbname" => "sample.db"
            )
        )
    );

    // Set a models manager
    $di->set('modelsManager', new ModelsManager());

    // Use the memory meta-data adapter or other
    $di->set('modelsMetadata', new MetaData());

    // Create a model
    class Robots extends Model
    {

    }

    // Use the model
    echo Robots::count();
