变量（Variables）
=================

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

`zval_copy_ctor_func` 实现：

.. code-block:: c

	ZEND_API void ZEND_FASTCALL _zval_copy_ctor_func(zval *zvalue ZEND_FILE_LINE_DC)
	{
		if (EXPECTED(Z_TYPE_P(zvalue) == IS_ARRAY)) {
			ZVAL_ARR(zvalue, zend_array_dup(Z_ARRVAL_P(zvalue)));
		} else if (EXPECTED(Z_TYPE_P(zvalue) == IS_STRING) ||
		           EXPECTED(Z_TYPE_P(zvalue) == IS_CONSTANT)) {
			CHECK_ZVAL_STRING_REL(Z_STR_P(zvalue));
			Z_STR_P(zvalue) = zend_string_dup(Z_STR_P(zvalue), 0);
		} else if (EXPECTED(Z_TYPE_P(zvalue) == IS_CONSTANT_AST)) {
			zend_ast *copy = zend_ast_copy(Z_ASTVAL_P(zvalue));
			ZVAL_NEW_AST(zvalue, copy);
		}
	}

变量的分离
----------
PHP7 中 提供 `SEPARATE_STRING`、`SEPARATE_ARRAY`、 `SEPARATE_ZVAL`与`SEPARATE_ZVAL_IF_NOT_REF`等宏定义来实现变量分离。
都会预先判断是否需要引用计数（IS_TYPE_REFCOUNTED）的类型，如果需要才会进行分离。

`SEPARATE_STRING`	- 如果类型是 IS_TYPE_REFCOUNTED 并且引用计数大于 1，将执行 `zval_copy_ctor_func`，并减少自身的引用计数。

`SEPARATE_ARRAY`	- 如果引用计数大于 1，将执行 `zval_copy_ctor_func`，如果类型不是不可变的（IS_TYPE_IMMUTABLE）将减少原有值的引用计数。

`SEPARATE_ZVAL`		- 如果引用计数大于 1，是可被复制的（IS_TYPE_COPYABLE）或是不可变的（IS_TYPE_IMMUTABLE）类型，将执行 `zval_copy_ctor_func`，如果是引用类型（IS_REFERENCE）的值将先减少自身的引用计数，然后使用 `ZVAL_DUP` 复制。

`SEPARATE_ZVAL_IF_NOT_REF`	- 如果类型是可被复制的（IS_TYPE_COPYABLE）或是不可变的（IS_TYPE_IMMUTABLE）类型，并且引用计数大于 1 将执行 `zval_copy_ctor_func`，如果是引用类型（IS_REFERENCE）的值将使用 `Z_DELREF_P｀ 先减少自身的引用计数
