常见的结构（Common Structures）
-------------------------------

To start explaining Phalcon, is necessary to understand a couple of low-level structures that are commonly used in
the framework:

变量（Zvals）
^^^^^^^^^^^^^
框架中最常用的变量是 zval。一个PHP应用程序中的每个值是一个变量。zval 是一个多态性结构，即一个 zval 变量可以是任何值（bool、string、long、double、array等）。
浏览 Phalcon7 内部的一些代码，你会看到，大多数变量的声明 zval。PHP具有标量数据类型和非标量数据类型（array 和 object）。下面演示如何给 zval 赋予不同类型的值：

.. code-block:: c

	zval name, numner, price, nothing, is_alive, imagick;

	ZVAL_STRING(&name, "Sonny");
	ZVAL_LONG(&number, 12000);
	ZVAL_DOUBLE(&price, 15.50);
	ZVAL_NULL(&nothing);
	ZVAL_BOOL(&is_alive, false);

	object_init_ex(&imagick, imagick_ce);

通常情况下，我们不会直接去改变 zval 内部变量，而是使用 Zend API 提供的方法进行管理。

让我看下如何获取 zval 变量的值：

.. code-block:: c

	char *str = Z_STRVAL(name);
	long number = Z_LVAL(numner);
	int bool_value = Z_BVA(is_alive);

如果您想知道 zval 值的类型：

.. code-block:: c

	int type = Z_TYPE(some_variable);
	if (type == IS_STRING) {
		// Is string!
	}

类的原型（Zend Class Entries）
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
该结构体帮助我们定义类，包括它的名字、方法、属性等等。

.. code-block:: c

	//Get the class entry
	class_entry = Z_OBJCE_P(this_ptr);

	//Print the class name
	fprintf(stdout, "%s", class_entry->name);
