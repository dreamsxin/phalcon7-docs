变量之间的操作（Operations between Variables）
==============================================
我们几乎可以做任何类型的两个变量之间的进行操作，当我们不知道确切的数据类型时，我们也可以使用 Zend API 操作它们。

.. code-block:: c

	// First variable is string but it's a numeric string
	ZVAL_STRING(&first_var, "100.10");

	// Second variable is long
	ZVAL_LONG(&second_var, 150);

	// add_function will make the necessary conversions to produce the addition
	add_function(&result, &first_var, &second_var);

连接（Concatenation）
---------------------
在 PHP 中连接操作是最频繁的操作之一，我一样可以使用 Zend API 简单实现多个值的拼接：

.. code-block:: c

	// The following concatention using just Zend API:
	//
	// $month = "July"; $day = 1;
	// $today = "Today is ".$month." ".$day;

	ZVAL_STRING(&month, "2012");

	ZVAL_LONG(&day, 1);

	ZVAL_STRING(&today_is, "Today is");

	concat_function(&first_part, &today_is, &month);

	ZVAL_STRING(&space, " ");

	concat_function(&second_part, &space, &day);

	concat_function(&today, &first_part, &second_part);

Another way to do that is use sprintf, in this case, you need to be completely sure that the variables have all string types:

.. code-block:: c

	char *final_string;
	zval final;

	ZVAL_STRING(&month, "2012");

	ZVAL_STRING(&day, "1");

	final_string = emalloc(sizeof(char)*(Z_STRLEN_P(month)+Z_STRLEN_P(day)+12)));
	sprintf(final_string, "Today is %s %s", Z_STRVAL_P(month), Z_STRVAL_P(day));

	ZVAL_STRING(&final, final_string);

常用函数列表
^^^^^^^^^^^^
Phalcon API 在 Zend API 的基础上提供更多的函数和弘定义（kernel/operators.h）。

+----------------------------+
| 函数名/宏名                |
+============================+
| phalcon_compare            |
+----------------------------+
| phalcon_is_equal           |
+----------------------------+
| phalcon_less               |
+----------------------------+
| phalcon_greater            |
+----------------------------+
| phalcon_is_scalar          |
+----------------------------+
| phalcon_get_intval         |
+----------------------------+

It's short, but if some of your variables aren't string you will get a segmentation fault or an unexpected behavior.

To help to solve this problem, we have created a set of macros to concatenate zvals and strings:

.. code-block:: c

	ZVAL_STRING(&month, "2012", 1);

	ZVAL_STRING(&day, "1", 1);

	PHALCON_CONCAT_SVSV(&today, "Today is", &month, " ", &day);

Other examples:

.. code-block:: c

	PHALCON_CONCAT_VV(&result, &month, &day); //July1
	PHALCON_CONCAT_VSV(&result, &month, ", ", &day); //July, 1
	PHALCON_CONCAT_SVSV(&result, "Today is", &month, " ", &day); //July 1
	PHALCON_CONCAT_SVSVSV(&result, "Today is", &month, " ", &day, ", ", &year); //July 1, 2012

S=String and V=Zval, just put the S and V to get the right concatenation macro. Easy, no?
