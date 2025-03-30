```
SharedArray{T}(dims::NTuple; init=false, pids=Int[])
SharedArray{T,N}(...)
```

构造一个位类型 `T` 的 `SharedArray`，大小为 `dims`，跨越由 `pids` 指定的进程 - 所有进程必须在同一主机上。如果通过调用 `SharedArray{T,N}(dims)` 指定了 `N`，则 `N` 必须与 `dims` 的长度匹配。

如果 `pids` 未指定，则共享数组将在当前主机上的所有进程中映射，包括主进程。但是，`localindices` 和 `indexpids` 仅会引用工作进程。这便于工作分配代码使用工作进程进行实际计算，而主进程充当驱动程序。

如果指定了类型为 `initfn(S::SharedArray)` 的 `init` 函数，则会在所有参与的工作进程上调用它。

只要在创建映射的节点上存在对 `SharedArray` 对象的引用，共享数组就是有效的。

```
SharedArray{T}(filename::AbstractString, dims::NTuple, [offset=0]; mode=nothing, init=false, pids=Int[])
SharedArray{T,N}(...)
```

构造一个由文件 `filename` 支持的 `SharedArray`，元素类型为 `T`（必须是位类型）和大小为 `dims`，跨越由 `pids` 指定的进程 - 所有进程必须在同一主机上。该文件被映射到主机内存中，具有以下后果：

  * 数组数据必须以二进制格式表示（例如，像 CSV 这样的 ASCII 格式不支持）
  * 你对数组值所做的任何更改（例如，`A[3] = 0`）也会更改磁盘上的值

如果 `pids` 未指定，则共享数组将在当前主机上的所有进程中映射，包括主进程。但是，`localindices` 和 `indexpids` 仅会引用工作进程。这便于工作分配代码使用工作进程进行实际计算，而主进程充当驱动程序。

`mode` 必须是 `"r"`、`"r+"`、`"w+"` 或 `"a+"` 之一，如果由 `filename` 指定的文件已存在，则默认为 `"r+"`，如果不存在，则默认为 `"w+"`。如果指定了类型为 `initfn(S::SharedArray)` 的 `init` 函数，则会在所有参与的工作进程上调用它。如果文件不可写，则不能指定 `init` 函数。

`offset` 允许你跳过文件开头指定数量的字节。
