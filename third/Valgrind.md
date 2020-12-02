

https://blog.csdn.net/u014470361/article/details/98384767

Valgrind的使用
Valgrind工具包包含多个工具，如Memcheck,Cachegrind,Helgrind, Callgrind，Massif。

Memcheck

最常用的工具，用来检测程序中出现的内存问题，所有对内存的读写都会被检测到，一切对malloc()/free()/new/delete的调用都会被捕获。所以，Memcheck 工具主要检查下面的程序错误。
(1)使用未初始化的内存 Use of uninitialised memory
(2)使用已经释放了的内存 Reading/writing memory after it has been free’d
(3)使用超过 malloc分配的内存空间 Reading/writing off the end of malloc’d blocks
(4)对堆栈的非法访问 Reading/writing inappropriate areas on the stack
(5)申请的空间是否有释放 Memory leaks – where pointers to malloc’d blocks are lost forever
(6)malloc/free/new/delete申请和释放内存的匹配 Mismatched use of malloc/new/new [] vs free/delete/delete []
(7)src和dst的重叠 Overlapping src and dst pointers in memcpy() and related functions
这些问题往往是C/C++程序员最头疼的问题，Memcheck在这里帮上了大忙。

Callgrind

和gprof类似的分析工具，但它对程序的运行观察更是入微，能给我们提供更多的信息。和gprof不同，它不需要在编译源代码时附加特殊选项，但加上调试选项是推荐的。Callgrind收集程序运行时的一些数据，建立函数调用关系图，还可以有选择地进行cache模拟。在运行结束时，它会把分析数据写入一个文件。callgrind_annotate可以把这个文件的内容转化成可读的形式。

Cachegrind

Cache分析器，它模拟CPU中的一级缓存I1，Dl和二级缓存，能够精确地指出程序中cache的丢失和命中。如果需要，它还能够为我们提供cache丢失次数，内存引用次数，以及每行代码，每个函数，每个模块，整个程序产生的指令数。这对优化程序有很大的帮助。

Helgrind

它主要用来检查多线程程序中出现的竞争问题。Helgrind寻找内存中被多个线程访问，而又没有一贯加锁的区域，这些区域往往是线程之间失去同步的地方，而且会导致难以发掘的错误。Helgrind实现了名为“Eraser”的竞争检测算法，并做了进一步改进，减少了报告错误的次数。不过，Helgrind仍然处于实验阶段。

Massif

堆栈分析器，它能测量程序在堆栈中使用了多少内存，告诉我们堆块，堆管理块和栈的大小。Massif能帮助我们减少内存的使用，在带有虚拟内存的现代系统中，它还能够加速我们程序的运行，减少程序停留在交换区中的几率。

用法: valgrind [options] prog-and-args
[options]: 常用选项，适用于所有Valgrind工具

-tool=<name> 最常用的选项。运行 valgrind中名为toolname的工具。默认memcheck。

    memcheck ------> 这是valgrind应用最广泛的工具，一个重量级的内存检查器，能够发现开发中绝大多数内存错误使用情况，比如：使用未初始化的内存，使用已经释放了的内存，内存访问越界等。

    callgrind ------> 它主要用来检查程序中函数调用过程中出现的问题。

    cachegrind ------> 它主要用来检查程序中缓存使用出现的问题。

    helgrind ------> 它主要用来检查多线程程序中出现的竞争问题。

    massif ------> 它主要用来检查程序中堆栈使用中出现的问题。

    extension ------> 可以利用core提供的功能，自己编写特定的内存调试工具

-h –help 显示帮助信息。
-version 显示valgrind内核的版本，每个工具都有各自的版本。
-q –quiet 安静地运行，只打印错误信息。
-v –verbose 更详细的信息, 增加错误数统计。
-trace-children=no|yes 跟踪子线程? [no]
-track-fds=no|yes 跟踪打开的文件描述？[no]
-time-stamp=no|yes 增加时间戳到LOG信息? [no]
-log-fd=<number> 输出LOG到描述符文件 [2=stderr]
-log-file=<file> 将输出的信息写入到filename.PID的文件里，PID是运行程序的进行ID
-log-file-exactly=<file> 输出LOG信息到 file
-log-file-qualifier=<VAR> 取得环境变量的值来做为输出信息的文件名。 [none]
-log-socket=ipaddr:port 输出LOG到socket ，ipaddr:port
