Phalcon7 核心开发手册
=====================

Phalcon7 是使用 C 语言开发的 PHP7 框架，本文档的目的是解释 Phalcon7 内部是如何运作，如果您对完善 Phalcon7 有兴趣或者想了解它是如何实现的，这里会有您需要的信息。

Phalcon API 说明
----------------
我们是 Phalcon 的创造者，主要是 PHP 程序员，我们很懒，不想花费 100% 的时间用在底层问题上，如段错误（segmentation faults）或内存泄漏（memory leaks）。我们相信 PHP 语言是令人难以置信的，Phalcon 实现我们每天都在做的事情，而且它可以更快。

此外，我们需要一个快速和稳定的框架。为此，我们创建了 Phalcon API。使用本 API 能帮助我们快速编写 C 代码。我们已经开发了一些函数来帮助开发者用更简单的方式编写 C 代码与 PHP 进行交互操作。

Phalcon API 基于 Zend API，但是我们增加了更多的功能，方便我们的开发。Phalcon 是一个非常大的项目，每一天都需要开发和改进框架，Phalcon API 帮助我们编写更加熟悉和稳定的 C 代码。
如果你是一个 PHP 开发人员，也许你不知道 C 或你不想学习 C，但阅读本指南后，你会发现 Phalcon API 在你对这些是非常熟悉的。

总则（General Considerations）
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
* 提供一个更容易被开发者理解的代码
* 创建尽可能接近 PHP 对象的对象和组件
* 尽量使用 Zend API 以及 PHP 内置方法
* 保证代码的可读性、可维护性

遵循以下指导守则：

* 最终实现的对象和组件要符合 PHP 风格。`Reflection <http://en.wikipedia.org/wiki/Reflection_%28computer_programming%29>`_
* 给使用者提供易于理解的回溯追踪。
* 如果 PHP 已经实现了一个功能，我没有理由不用它。`Don't repeat yourself <http://en.wikipedia.org/wiki/Don%27t_repeat_yourself>`_

目录（Table of Contents）
-------------------------

.. toctree::
   :maxdepth: 1

   structures
   memory
   variables
   operations
   arrays
   functions
   objects
   methods
   classes
   exceptions
   requires

声明
^^^^

.. toctree::
   :maxdepth: 1

   license
