```
GC.safepoint()
```

在程序中插入一个垃圾收集可能运行的点。这在多线程程序中是有用的，某些线程正在分配内存（因此可能需要运行垃圾收集），而其他线程仅执行简单操作（没有分配、任务切换或 I/O）。在不分配内存的线程中定期调用此函数允许垃圾收集运行。

!!! compat "Julia 1.4"
    此函数从 Julia 1.4 开始可用。

