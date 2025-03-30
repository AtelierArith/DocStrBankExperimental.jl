```
@time_imports
```

一个宏，用于执行一个表达式并生成任何导入包及其依赖项所花费时间的报告。任何编译时间将以百分比形式报告，以及其中有多少是重新编译（如果有的话）。

每个包或包扩展都会打印一行。显示的持续时间是导入该包本身所需的时间，不包括加载其任何依赖项的时间。

在 Julia 1.9+ 中，[包扩展](@ref man-extensions) 将显示为 Parent → Extension。

!!! note
    在加载过程中，一个包会顺序导入其所有依赖项，而不仅仅是其直接依赖项。


```julia-repl
julia> @time_imports using CSV
     50.7 ms  Parsers 17.52% compilation time
      0.2 ms  DataValueInterfaces
      1.6 ms  DataAPI
      0.1 ms  IteratorInterfaceExtensions
      0.1 ms  TableTraits
     17.5 ms  Tables
     26.8 ms  PooledArrays
    193.7 ms  SentinelArrays 75.12% compilation time
      8.6 ms  InlineStrings
     20.3 ms  WeakRefStrings
      2.0 ms  TranscodingStreams
      1.4 ms  Zlib_jll
      1.8 ms  CodecZlib
      0.8 ms  Compat
     13.1 ms  FilePathsBase 28.39% compilation time
   1681.2 ms  CSV 92.40% compilation time
```

!!! compat "Julia 1.8"
    此宏至少需要 Julia 1.8

