常见的结构（Common Structures）
===============================

首先让我们来了解一些底层的常用的结构。

变量（Zvals）
-------------
框架中最常用的变量是 zval。一个PHP应用程序中的每个值是一个变量。zval 是一个多态性结构，即一个 zval 变量可以是任何值（bool、string、long、double、array等）。
浏览 Phalcon7 内部的一些代码，你会看到，大多数变量的声明 zval。PHP具有标量数据类型和非标量数据类型（array 和 object）。


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
	#define IS_INDIRECT                 15 //间接变量，跟 compiled variables(CV) table 有关系
	#define IS_PTR                      17

标志位
^^^^^^
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

下面演示如何给 zval 赋予不同类型的值：

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

哈希表（HashTable）
-------------------
哈希表是 PHP 内部非常重要的数据结构，除了最常见的数组，内核也随处用到，比如 function、class 的索引、符号表等等都用到了哈希表。

.. code-block:: c

	typedef struct _Bucket {
	    zval              val;
	    zend_ulong        h;                /* hash value (or numeric index)   */
	    zend_string      *key;              /* string key or NULL for numerics */
	} Bucket;

	typedef struct _zend_array HashTable;

	struct _zend_array {
	    zend_refcounted_h gc;
	    union {
	        struct {
	            ZEND_ENDIAN_LOHI_4(
	                    zend_uchar    flags,
	                    zend_uchar    nApplyCount,
	                    zend_uchar    nIteratorsCount,
	                    zend_uchar    reserve)
	        } v;
	        uint32_t flags;
	    } u;
	    uint32_t          nTableMask;		// 哈希值计算掩码，等于nTableSize的负值(nTableMask = ~nTableSize + 1)
	    Bucket           *arData;			// 存储元素数组，指向第一个Bucket
	    uint32_t          nNumUsed;			// 已用Bucket数
	    uint32_t          nNumOfElements;	// 哈希表已有元素数
	    uint32_t          nTableSize;		// 哈希表总大小，为2的n次方
	    uint32_t          nInternalPointer;
	    zend_long         nNextFreeElement; // 下一个可用的数值索引,如:arr[] = 1;arr["a"] = 2;arr[] = 3;  则nNextFreeElement = 2;
	    dtor_func_t       pDestructor;
	};

哈希碰撞
^^^^^^^^

哈希碰撞是指不同的key可能计算得到相同的哈希值(数值索引的哈希值直接就是数值本身)，但是这些值又需要插入同一个哈希表。一般解决方法是将Bucket串成链表，查找时遍历链表比较key。

PHP的实现也是类似，只是指向冲突元素的指针并没有直接存在Bucket中，而是存在嵌入的zval中，zval的结构：

.. code-block:: c

	struct _zval_struct {
	    zend_value        value;            /* value */
	    union {
	        struct {
	            ZEND_ENDIAN_LOHI_4(
	                    zend_uchar    type,         /* active type */
	                    zend_uchar    type_flags,
	                    zend_uchar    const_flags,
	                    zend_uchar    reserved)     /* call info for EX(This) */
	        } v;
	        uint32_t type_info;
	    } u1;
	    union {
	        uint32_t     var_flags;
	        uint32_t     next;                 /* hash collision chain */
	        uint32_t     cache_slot;           /* literal cache slot */
	        uint32_t     lineno;               /* line number (for ast nodes) */
	        uint32_t     num_args;             /* arguments number for EX(This) */
	        uint32_t     fe_pos;               /* foreach position */
	        uint32_t     fe_iter_idx;          /* foreach iterator index */
	    } u2;
	};

HashTable 中有两个非常相近的值：nNumUsed、nNumOfElements，nNumOfElements表示哈希表已有元素数，那这个值不跟nNumUsed一样吗？为什么要定义两个呢？实际上它们有不同的含义，当将一个元素从哈希表删除时并不会将对应的Bucket移除，而是将Bucket存储的zval标示为IS_UNDEF，只有扩容时发现nNumOfElements与nNumUsed相差达到一定数量(这个数量是:ht->nNumUsed - ht->nNumOfElements > (ht->nNumOfElements >> 5))时才会将已删除的元素全部移除，重新构建哈希表。所以nNumUsed>=nNumOfElements。

HashTable 中另外一个非常重要的值 arData，这个值指向存储元素数组的第一个Bucket，插入元素时按顺序依次插入数组，比如第一个元素在arData[0]、第二个在arData[1]…arData[nNumUsed]。PHP数组的有序性正是通过arData保证的。

zval.u2.next 存的就是冲突元素在Bucket数组中的位置，所以查找过程类似：

.. code-block:: c

	zend_ulong h = zend_string_hash_val(key);
	uint32_t idx = ht->arHash[h & ht->nTableMask];
	while (idx != INVALID_IDX) {
	    Bucket *b = &ht->arData[idx];
	    if (b->h == h && zend_string_equals(b->key, key)) {
	        return b;
	    }
	    idx = Z_NEXT(b->val); // b->val.u2.next
	}
	return NULL;

类的原型（Zend Class Entries）
------------------------------
该结构体帮助我们定义类，包括它的名字、方法、属性等等。

.. code-block:: c

	//Get the class entry
	class_entry = Z_OBJCE_P(this_ptr);

	//Print the class name
	fprintf(stdout, "%s", class_entry->name);

类的标准操作集合（handlers）
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code-block:: c

	struct _zend_object {
		zend_refcounted_h gc;
		uint32_t          handle; // TODO: may be removed ???
		zend_class_entry *ce;
		const zend_object_handlers *handlers;
		HashTable        *properties;
		zval              properties_table[1];
	};

	struct _zend_object_handlers {
		/* offset of real object header (usually zero) */
		int										offset;
		/* general object functions */
		zend_object_free_obj_t					free_obj;
		zend_object_dtor_obj_t					dtor_obj;
		zend_object_clone_obj_t					clone_obj;
		/* individual object functions */
		zend_object_read_property_t				read_property;
		zend_object_write_property_t			write_property;
		zend_object_read_dimension_t			read_dimension;
		zend_object_write_dimension_t			write_dimension;
		zend_object_get_property_ptr_ptr_t		get_property_ptr_ptr;
		zend_object_get_t						get;
		zend_object_set_t						set;
		zend_object_has_property_t				has_property;
		zend_object_unset_property_t			unset_property;
		zend_object_has_dimension_t				has_dimension;
		zend_object_unset_dimension_t			unset_dimension;
		zend_object_get_properties_t			get_properties;
		zend_object_get_method_t				get_method;
		zend_object_call_method_t				call_method;
		zend_object_get_constructor_t			get_constructor;
		zend_object_get_class_name_t			get_class_name;
		zend_object_compare_t					compare_objects;
		zend_object_cast_t						cast_object;
		zend_object_count_elements_t			count_elements;
		zend_object_get_debug_info_t			get_debug_info;
		zend_object_get_closure_t				get_closure;
		zend_object_get_gc_t					get_gc;
		zend_object_do_operation_t				do_operation;
		zend_object_compare_zvals_t				compare;
	};