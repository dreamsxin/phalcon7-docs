变量（Variables）
=================
PHP7中的zval的类型做了比较大的调整, 总体来说有如下17种类型:

.. code-block:: c

	/* regular data types */
	#define IS_UNDEF                    0
	#define IS_NULL                     1
	#define IS_FALSE                    2
	#define IS_TRUE                     3
	#define IS_LONG                     4
	#define IS_DOUBLE                   5
	#define IS_STRING                   6
	#define IS_ARRAY                    7
	#define IS_OBJECT                   8
	#define IS_RESOURCE                 9
	#define IS_REFERENCE                10

	/* constant expressions */
	#define IS_CONSTANT                 11
	#define IS_CONSTANT_AST             12

	/* fake types */
	#define _IS_BOOL                    13
	#define IS_CALLABLE                 14

	/* internal types */
	#define IS_INDIRECT                 15
	#define IS_PTR                      17

标志位
------
作用于zval的有：

.. code-block:: c

	#define IS_TYPE_CONSTANT            //是常量类型
	#define IS_TYPE_IMMUTABLE           //不可变的类型， 比如存在共享内存的数组
	#define IS_TYPE_REFCOUNTED          //需要引用计数的类型
	#define IS_TYPE_COLLECTABLE         //可能包含循环引用的类型(IS_ARRAY, IS_OBJECT)
	#define IS_TYPE_COPYABLE            //可被复制的类型， 还记得我之前讲的对象和资源的例外么？ 对象和资源就不是
	#define IS_TYPE_SYMBOLTABLE         //zval保存的是全局符号表， 这个在我之前做了一个调整以后没用了， 但还保留着兼容，下个版本会去掉

作用于字符串的有:

.. code-block:: c

	#define IS_STR_PERSISTENT	        //是malloc分配内存的字符串
	#define IS_STR_INTERNED             //INTERNED STRING
	#define IS_STR_PERMANENT            //不可变的字符串， 用作哨兵作用
	#define IS_STR_CONSTANT             //代表常量的字符串
	#define IS_STR_CONSTANT_UNQUALIFIED //带有可能命名空间的常量字符串

作用于数组的有:

.. code-block:: c

	#define IS_ARRAY_IMMUTABLE  //同IS_TYPE_IMMUTABLE

作用于对象的有：

.. code-block:: c

	#define IS_OBJ_APPLY_COUNT          //递归保护
	#define IS_OBJ_DESTRUCTOR_CALLED    //析构函数已经调用
	#define IS_OBJ_FREE_CALLED          //清理函数已经调用
	#define IS_OBJ_USE_GUARDS           //魔术方法递归保护
	#define IS_OBJ_HAS_GUARDS           //是否有魔术方法递归保护标志

创建（Creation）
----------------
与 PHP 不同，C 中的每个变量必须在我们函数的开头声明，在使用前必须初始化。甚至，当我们改变它的时候，它应该再次被重新初始化，例如：

.. code-block:: c

	// Declare the variable and initialize the variable
	zval some_number = {};

	// Assign it a string value
	ZVAL_STRING(some_number, "one hundred");

	// Reinitialize the variable and change its value to long
	PHALCON_INIT_NVAR(some_number);
	ZVAL_LONG(some_number, 100);

If a variable is assigned within a cycle or it's re-assigned is important to initialize it to NULL in its declaration.
By doing this, PHALCON_INIT_NVAR will know if the variable needs memory or it already have memory allocated.

变量的复制
----------
PHP7 中 提供 `ZVAL_COPY_VALUE`、`ZVAL_COPY`与 `ZVAL_DUP`等宏定义来实现变量的复制。

.. code-block:: c

	zval a = {}, b = {}, c = {};

	ZVAL_LONG(&a, 1500);

	// 复制
	ZVAL_COPY_VALUE(&b, &a);

	// 在 ZVAL_COPY_VALUE 的基础上，复制并增加 a 引用计数，不过对不是 IS_TYPE_REFCOUNTED 的不会增加引用计数
	ZVAL_COPY(&b, &a);

	// 在 ZVAL_COPY_VALUE 的基础上，如果类型是需要引用计数（IS_TYPE_REFCOUNTED）会增加自身引用计数
	// 如果是可被复制的（IS_TYPE_COPYABLE）或不可变的（IS_TYPE_IMMUTABLE）的类型，会执行 `zval_copy_ctor_func`
	array_init(&c);
	ZVAL_DUP(&a, &c);

变量的分离
----------
PHP7 中 提供 `SEPARATE_STRING`、`SEPARATE_ARRAY`、 `SEPARATE_ZVAL`与`SEPARATE_ZVAL_IF_NOT_REF`等宏定义来实现变量分离。
都会预先判断是否需要引用计数（IS_TYPE_REFCOUNTED）的类型，如果需要才会进行分离。

`SEPARATE_STRING` - 如果类型是 IS_TYPE_REFCOUNTED 并且引用计数大于 1，将执行 `zval_copy_ctor_func`，并减少自身的引用计数。

`SEPARATE_ARRAY` - 如果引用计数大于 1，将执行 `zval_copy_ctor_func`，如果类型不是不可变的（IS_TYPE_IMMUTABLE）将减少原有值的引用计数。

`SEPARATE_ZVAL` - 如果引用计数大于 1，是可被复制的（IS_TYPE_COPYABLE）或是不可变的（IS_TYPE_IMMUTABLE）类型，将执行 `zval_copy_ctor_func`，如果是引用类型（IS_REFERENCE）的值将先减少自身的引用计数，然后使用 `ZVAL_DUP` 复制。
