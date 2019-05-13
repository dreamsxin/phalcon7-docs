分布式自增 ID（Snowflake）
==========================
Phalcon 提供了 :doc:`Phalcon\\Snowflake <../api/Phalcon_Snowflake>` 类来生成自增ID。

.. code-block:: php

    <?php

    $snowflake = new Phalcon\Snowflake;
    $id = $snowflake->nextId();
    $desc = $snowflake->parse($id)

.. highlights::

    多台服务器，需要在配置文件中设置不同的 `phalcon.snowflake.node`，默认为 0。

利用分布式 ID 实现分库分表
--------------------------
Twitter-Snowflake 算法产生的背景相当简单，为了满足 Twitter 每秒上万条消息的请求，每条消息都必须分配一条唯一的id。
这些 ID 还需要一些大致的顺序（方便客户端排序），并且在分布式系统中不同机器产生的 ID 必须不同。

二叉树分库分表
^^^^^^^^^^^^^^

所谓 “二叉树分库分表” 指的是：
在进行数据库扩容时，都是以2倍数进行扩容（初始值一定要是2的N次方，一般默认初始为16），这种分库方式的好处是，在进行扩容时，只需进行表级的数据同步。

.. highlights::

    当 length 一定是 2^n 时，h & (length - 1) == h % length，效率杠杠的。

假设原来分成两个库，假设按照hash的方式分片。那么结果分为奇数库1和偶数库0。
现在变成4个分片，这个过程没有数据的迁移，属于整库拷贝。原来偶数库变成了0和2，奇数的部分现在变成1和3。然后进行多余数据删除即可。

.. highlights::

    这里的扩容就是一个删数据过程而不是迁移数据过程，理论上可以无限横向扩展

生成分布式 ID：

.. code-block:: php

    <?php

    $snowflake = new Phalcon\Snowflake;
    $id = $snowflake->nextId();

按照生成的分布式 ID 进行分库，每个分库下再根据 分布式 ID 进行分表
按照项目的粒度进行分库，本例假设 8 台数据库服务器，每个分库下又分为了8张表，编号统一从 0 开始。

.. highlights::

    如果直接对 ID % 8 的话，以后在进行扩容的时候（增加至 16 台），分库路由将会无法正确地工作。为了解决此问题，我们需要对分库精度进行冗余，也就是说一开始就使用最大支持的分库数量来进行取模。


.. code-block:: php

    <?php

    $dbName = ($id % 64) % 8;
    $tableName = $id % 8;

注意事项（Troubleshooting）
---------------------------

* Failed to create shared memory (3)
如果出现此类错误，先查看目录`/dev/shm/` 是否存在文件 `phalcon_snowflake` 和 `sem.phalcon_snowflake`，如果存在删除即可。

