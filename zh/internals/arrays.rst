数组（Working with Arrays）
===========================
尽管 Zend API 提供了一些函数来处理数组，但 Phalcon API 中在此基础上封装了更多的函数（kernel/array.h），自动处理引用计数：

一维数组（One dimension Arrays）
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code-block:: c

	zval fruits = {}, first_item = {};

	array_init(&fruits);

	// Adding items to the array
	add_next_index_stringl(&fruits, SL("apple"));
	add_next_index_stringl(&fruits, SL("orange"));
	add_next_index_stringl(&fruits, SL("lemon"));
	add_next_index_stringl(&fruits, SL("banana"));

	phalcon_array_append_str(&fruits, SL("pear"), 0);

	// Get the first item in the array $fruits[0]
	phalcon_array_fetch_long(&first_item, &fruits, 0, PH_NOISY_CC);

Mixing both string and number indexes:

.. code-block:: c

	// Let's create the following array using the Phalcon API
	// $fruits = array(1, null, false, "some string", 15.20, "my-index" => "another string");

	array_init(&fruits);
	add_next_index_long(&fruits, 1);
	add_next_index_null(&fruits);
	add_next_index_bool(&fruits, 0);
	add_next_index_stringl(&fruits, SL("some string"));
	add_next_index_double(&fruits, 15.2);
	add_assoc_stringl_ex(&fruits, SL("my-index")+1, SL("another string"));

	// Updating an existing index $fruits[2] = "other value";
	phalcon_array_update_long_string(&fruits, 2, SL("other value"), PH_SEPARATE);

	// Removing an existing index unset($fruits[1]);
	phalcon_array_unset_long(fruits, 1);

	// Removing an existing index unset($fruits["my-index"]);
	phalcon_array_unset_string(fruits, SL("my-index")+1);
