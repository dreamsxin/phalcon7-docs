内存管理（Memory Management）
=============================
正如你可能知道，C 是所有的内存是自己维护管理的，而在 PHP 扩展中，所有的内存管理由 Zend Memory Manager 管理。

在 PHP7 中 zval 有了新的实现方式。最基础的变化就是 zval 需要的内存不再是单独从堆上分配，不再自己存储引用计数。复杂数据类型（比如字符串、数组和对象）的引用计数由其自身来存储。
这种实现方式有以下好处：
简单数据类型不需要单独分配内存，也不需要计数；
不会再有两次计数的情况。在对象中，只有对象自身存储的计数是有效的；
由于现在计数由数值自身存储，所以也就可以和非 zval 结构的数据共享，比如 zval 和 hashtable key 之间；
间接访问需要的指针数减少了。

For example:

.. code-block:: c

	PHP_METHOD(Phalcon_Some_Component, sayHello){

		zval greeting = {};

		ZVAL_STRING(&greeting, "Hello!");

		PHALCON_PTR_DTOR(&greeting);
	}

常用的内存接口
--------------
在扩展中不能使用标准函数 malloc 和 free，而是使用 Zend API 其提供的方法，使内存分配和使用更加安全，常用的方法有：

`emalloc(size)`、`safe_emalloc(nmemb, size, offset)`、`efree(ptr)`、`ecalloc(nmemb, size)`、`erealloc(ptr, size)`、
`safe_erealloc(ptr, nmemb, size, offset)`、`estrdup(s)`、`estrndup(s, length)`。

例子：
.. code-block:: c

	char *some_word = (char *) emalloc(sizeof(char *) * 6);
	memcpy(some_word, "Hello", 5);
	some_word[5] = 0;
	efree(some_word);

总之, `emalloc` 分配内存，以及使用 efree 释放内存，如果你忘记释放它们，将发生内存溢出。
