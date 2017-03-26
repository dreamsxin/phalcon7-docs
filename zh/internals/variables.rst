变量（Variables）
=================

创建（Creation）
----------------
Unlike PHP, each variable in C must be declared at the beginning of the function in which we are working. Also,
as noted above, all variables must be initialized before the use. Even, it should be reset again when we change its
value, for example:

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

Copy-on-Write
-------------
All the zval variables that we use in Phalcon are pointers. Each pointer points to its value in memory. Two pointers
may eventually point to the same value in memory:

.. code-block:: c

	zval a = {}, *b = NULL;

	ZVAL_LONG(&a, 1500);

	b = a;

	//Print both zvals print the same value
	zend_print_zval(&a, 1); // 1500
	zend_print_zval(b, 1); // 1500

Changing the value of any of the two variables will change both pointers because their value are the same:

.. code-block:: c

	ZVAL_LONG(b, -10);

	//Print both zvals print the same value
	zend_print_zval(&a, 1); // -10
	zend_print_zval(b, 1); // -10

Now, imagine the following PHP code:

.. code-block:: php

	<?php

	$a = 1500;
	$b = $a;

	echo $a, $b; // 1500 1500

This is practically the same as we did before, however, let's change the value of $b:

.. code-block:: php

	<?php

	$a = 1500;
	$b = $a;

	echo $a, $b; // 1500 1500

	$b = -10;

	echo $a, $b; // 1500 -10

To our eyes, PHP has done what we did in C, but in reality there has been an internal process called copy-on-write.  Pretend that our main memory is this:

.. code-block:: php

    // $a = "hello"
                +---------+----+
                |   0x1   | RC |
                +---------+----+
    zval *a --> | "hello" |  1 |
                +---------+----+

The variable $a is pointing to a virtual memory address 0x1, also that memory have a reference counting of 1. It means that only one variable
it's pointing to that memory address.

.. code-block:: php

    // $b = $a
                +---------+----+
                |   0x1   | RC |
                +---------+----+
    zval *a --> | "hello" |  2 |
                +---------+----+
    zval *b ---------^

Now, $b is equal to $a, now both variables are pointing to the same memory address 0x1. The reference counting is now 2, because two variables
are pointing to the same memory slot. As you can see PHP is saving memory, although the variables have different names, they're pointing to the same value in memory so that we are not unnecessarily doubling its value.

.. code-block:: php

    // $b = 18
                +---------+----+  +---------+----+
                |   0x1   | RC |  |   0x2   | RC |
                +---------+----+  +---------+----+
    zval *a --> | "hello" |  1 |  |    18   |  1 |
                +---------+----+  +---------+----+
    zval *b ----------------------------^

We are changing the variable $b, to avoid changing the value of $a, PHP performs an internal process called "separation". In this process, PHP allocates memory for $b and reduces the reference count in $a to indicate that $b is not pointing anymore to $a.

Let's see how to write the above process using Zend API:

.. code-block:: c

    zval a = {}, b = {};

    ZVAL_STRING(&a, "hello");

    ZVAL_COPY_VALUE(&b, a);

    SEPARATE_STRING(&b);
    ZVAL_LONG(&b, 18);
