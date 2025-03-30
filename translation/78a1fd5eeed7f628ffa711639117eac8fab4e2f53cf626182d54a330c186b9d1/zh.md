```
success(command)
```

运行一个命令对象，该对象使用反引号构造（请参见手册中的 [Running External Programs](@ref) 部分），并告知其是否成功（以代码 0 退出）。如果无法启动该进程，将引发异常。
