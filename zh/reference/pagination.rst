分页（Pagination）
==================

当需要呈现大量数据时我们需要用到该分页组件。:code:`Phalcon\Paginator` 提供了便捷数据集访问接口。

数据适配器（Data Adapters）
---------------------------
This component makes use of adapters to encapsulate different sources of data:

+---------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
| Adapter                                                             | Description                                                                                                                                               |
+=====================================================================+===========================================================================================================================================================+
| :doc:`NativeArray <../api/Phalcon_Paginator_Adapter_NativeArray>`   | 使用数组当数据源。                                                                                                                                        |
+---------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
| :doc:`Model <../api/Phalcon_Paginator_Adapter_Model>`               | 使用模型结果集 :doc:`Phalcon\\Mvc\\Model\\Resultset <../api/Phalcon_Mvc_Model_Resultset>` 当数据源。因为 PDO 不支持游标，所以不适合大数据量的翻页。       |
+---------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
| :doc:`QueryBuilder <../api/Phalcon_Paginator_Adapter_QueryBuilder>` | 使用查询构建器 :doc:`Phalcon\\Mvc\\Model\\Query\\Builder <../api/Phalcon_Mvc_Model_Query_Builder>` 当数据源                                               |
+---------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
| :doc:`DbBuilder <../api/Phalcon_Paginator_Adapter_DbBuilder>`       | 使用构建器     :doc:`Phalcon\\Db\\Builder\\Select <../api/Phalcon_Db_Builder_Select>` 当数据源                                                            |
+---------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
| :doc:`Sql <../api/Phalcon_Paginator_Adapter_Sql>`                   | 通过设置原生 SQL 获取数据源。                                                                                                                             |
+---------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+

示例（Examples）
----------------
In the example below, the paginator will use the result of a query from a model as its source data, and limit the displayed data to 10 records per page:

.. code-block:: php

    <?php

    use Phalcon\Paginator\Adapter\Model as PaginatorModel;

    // Current page to show
    // In a controller this can be:
    // $this->request->getQuery('page', 'int'); // GET
    // $this->request->getPost('page', 'int'); // POST
    $currentPage = (int) $_GET["page"];

    // The data set to paginate
    $robots      = Robots::find();

    // Create a Model paginator, show 10 rows by page starting from $currentPage
    $paginator   = new PaginatorModel(
        array(
            "data"  => $robots,
            "limit" => 10,
            "page"  => $currentPage
        )
    );

    // Get the paginated results
    $page = $paginator->getPaginate();

The :code:`$currentPage` variable controls the page to be displayed. The :code:`$paginator->getPaginate()` returns a :code:`$page`
object that contains the paginated data. It can be used for generating the pagination:

.. code-block:: html+php

    <table>
        <tr>
            <th>Id</th>
            <th>Name</th>
            <th>Type</th>
        </tr>
        <?php foreach ($page->items as $item) { ?>
        <tr>
            <td><?php echo $item->id; ?></td>
            <td><?php echo $item->name; ?></td>
            <td><?php echo $item->type; ?></td>
        </tr>
        <?php } ?>
    </table>

The :code:`$page` object also contains navigation data:

.. code-block:: html+php

    <a href="/robots/search">First</a>
    <a href="/robots/search?page=<?= $page->before; ?>">Previous</a>
    <a href="/robots/search?page=<?= $page->next; ?>">Next</a>
    <a href="/robots/search?page=<?= $page->last; ?>">Last</a>

    <?php echo "You are in page ", $page->current, " of ", $page->total_pages; ?>

适配器使用（Adapters Usage）
----------------------------
An example of the source data that must be used for each adapter:

.. code-block:: php

    <?php

    use Phalcon\Paginator\Adapter\Model as PaginatorModel;
    use Phalcon\Paginator\Adapter\NativeArray as PaginatorArray;
    use Phalcon\Paginator\Adapter\QueryBuilder as PaginatorQueryBuilder;
    use Phalcon\Paginator\Adapter\Sql as PaginatorSql;

    // Passing a resultset as data
    $paginator = new PaginatorModel(
        array(
            "data"  => Products::find(),
            "limit" => 10,
            "page"  => $currentPage
        )
    );

    // Passing an array as data
    $paginator = new PaginatorArray(
        array(
            "data"  => array(
                array('id' => 1, 'name' => 'Artichoke'),
                array('id' => 2, 'name' => 'Carrots'),
                array('id' => 3, 'name' => 'Beet'),
                array('id' => 4, 'name' => 'Lettuce'),
                array('id' => 5, 'name' => '')
            ),
            "limit" => 2,
            "page"  => $currentPage
        )
    );

    // Passing a QueryBuilder as data

    $builder = $this->modelsManager->createBuilder()
        ->columns('id, name')
        ->from('Robots')
        ->orderBy('name');

    $paginator = new PaginatorQueryBuilder(
        array(
            "builder" => $builder,
            "limit"   => 20,
            "page"    => 1
        )
    );

    $paginator = new PaginatorSql(
        array(
            "sql" => "SELECT * FROM robots WHERE type = :type LIMIT :limit OFFSET :offset",
            "total_sql" => "SELECT COUNT(*) rowcount FROM robots WHERE type = :type",
	        "bind" => ['type' => 'google'],
            "limit"   => 20,
            "page"    => 1
        )
    );

页面属性（Page Attributes）
---------------------------
The :code:`$page` object has the following attributes:

+-------------+--------------------------------------------------------+
| Attribute   | Description                                            |
+=============+========================================================+
| items       | The set of records to be displayed at the current page |
+-------------+--------------------------------------------------------+
| current     | The current page                                       |
+-------------+--------------------------------------------------------+
| before      | The previous page to the current one                   |
+-------------+--------------------------------------------------------+
| next        | The next page to the current one                       |
+-------------+--------------------------------------------------------+
| last        | The last page in the set of records                    |
+-------------+--------------------------------------------------------+
| total_pages | The number of pages                                    |
+-------------+--------------------------------------------------------+
| total_items | The number of items in the source data                 |
+-------------+--------------------------------------------------------+

自定义适配器（Implementing your own adapters）
----------------------------------------------
The :doc:`Phalcon\\Paginator\\AdapterInterface <../api/Phalcon_Paginator_AdapterInterface>` interface must be implemented in order to create your own paginator adapters or extend the existing ones:

.. code-block:: php

    <?php

    use Phalcon\Paginator\AdapterInterface as PaginatorInterface;

    class MyPaginator implements PaginatorInterface
    {
        /**
         * Adapter constructor
         *
         * @param array $config
         */
        public function __construct($config);

        /**
         * Set the current page number
         *
         * @param int $page
         */
        public function setCurrentPage($page);

        /**
         * Returns a slice of the resultset to show in the pagination
         *
         * @return stdClass
         */
        public function getPaginate();
    }
