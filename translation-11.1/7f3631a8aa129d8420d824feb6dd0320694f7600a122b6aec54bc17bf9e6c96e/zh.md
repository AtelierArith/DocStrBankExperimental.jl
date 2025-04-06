```
open(fd::OS_HANDLE) -> IO
```

将原始文件描述符包装在一个Julia感知的IO类型中，并接管fd句柄的所有权。调用`open(Libc.dup(fd))`以避免原始句柄的所有权捕获。

!!! warning
    不要在系统中已经被其他部分拥有的句柄上调用此函数。

