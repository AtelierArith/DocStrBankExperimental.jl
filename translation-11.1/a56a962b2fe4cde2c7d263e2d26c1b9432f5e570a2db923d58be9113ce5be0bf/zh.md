```
varinfo(m::Module=Main, pattern::Regex=r""; all=false, imported=false, recursive=false, sortby::Symbol=:name, minsize::Int=0)
```

返回一个 Markdown 表格，提供有关模块中公共全局变量的信息，选项上可以限制为匹配 `pattern` 的变量。

内存消耗估计是对象内部结构大小的近似下限。

  * `all` : 还列出模块中定义的非公共对象、已弃用对象和编译器生成的对象。
  * `imported` : 还列出从其他模块显式导入的对象。
  * `recursive` : 递归包含子模块中的对象，在每个子模块中遵循相同的设置。
  * `sortby` : 用于排序结果的列。选项为 `:name`（默认）、`:size` 和 `:summary`。
  * `minsize` : 仅包括大小至少为 `minsize` 字节的对象。默认为 `0`。

`varinfo` 的输出仅用于显示目的。另请参见 [`names`](@ref) 以获取模块中定义的符号数组，适合进行更一般的操作。
