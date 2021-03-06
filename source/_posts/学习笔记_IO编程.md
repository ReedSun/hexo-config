﻿title: 学习笔记_IO编程
date: 2016/09/29 21:46:20
tags: Python
---

- IO在计算机中指Input/Output，也就是输入和输出。由于程序和运行时数据是在内存中驻留，由CPU这个超快的计算核心来执行，涉及到数据交换的地方，通常是磁盘、网络等，就需要IO接口。

- IO编程中，Stream（流）是一个很重要的概念，可以把流想象成一个水管，数据就是水管里的水，但是只能单向流动。Input Stream就是数据从外面（磁盘、网络）流进内存，Output Stream就是数据从内存流到外面去。对

- IO编程又分为同步IO和异步IO，我们本章讨论的都是同步IO，异步IO性能比同步IO好很多，但是比较复杂，后续涉及到服务器端开发时候再讨论。
  - 同步IO：程序执行到IO时，暂停后续代码，等数据读写完毕，再继续执行后续代码。
  - 异步IO：程序执行到IO时，后续代码可以继续执行，不用等待数据读写完毕。

##读写

###文档读写

- 在python中，文档读写是通过`open()`加不同的标识符实现的，要注意在操作文档读写时使用with语句的好习惯。

### StringIO和BytesIO

- `StringIO`和`BytesIO`本质上是两个class类，我们要读写它们还是要是用`write()`方法。

- `StringIO`和`BytesIO`是在内存中操作`str`和`bytes`的方法，使得和读写文件具有一致的接口。

##操作文件和目录

- Python的`os`模块封装了操作系统的目录和文件操作，要注意这些函数有的在`os`模块中，有的在`os.path`模块中。

##序列化

- 我们把变量从内存中变成可存储或传输的过程称之为序列化，在Python中叫pickling。

- 把变量内容从序列化的对象重新读到内存里称之为反序列化，即unpickling。

- JSON(JavaScript Object Notation) 是一种轻量级的数据交换格式。它基于ECMAScript的一个子集。 JSON采用完全独立于语言的文本格式，但是也使用了类似于C语言家族的习惯（包括C、C++、C#、Java、JavaScript、Perl、Python等）。这些特性使JSON成为理想的数据交换语言。 易于人阅读和编写，同时也易于机器解析和生成(一般用于提升网络传输速率)。**捡重点说！JSON就是一个标准的格式，便于在各个编程语言之间交流和传递对象**

- Python语言特定的序列化模块是`pickle`，但如果要把序列化搞得更通用、更符合Web标准，就可以使用`json`模块。

- json模块的`dumps()`和`loads()`函数是定义得非常好的接口的典范。当我们使用时，只需要传入一个必须的参数。但是，当默认的序列化或反序列机制不满足我们的要求时，我们又可以传入更多的参数来定制序列化或反序列化的规则，既做到了接口简单易用，又做到了充分的扩展性和灵活性。

  