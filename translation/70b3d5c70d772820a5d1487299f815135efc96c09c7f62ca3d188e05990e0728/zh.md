```
Sys.isnetbsd([os])
```

用于测试操作系统是否是 NetBSD 的派生版本的谓词。请参阅 [处理操作系统变异](@ref) 中的文档。

!!! note
    不要与 `Sys.isbsd()` 混淆，后者在 NetBSD 上为 `true`，但在其他基于 BSD 的系统上也为 `true`。`Sys.isnetbsd()` 仅指 NetBSD。


!!! compat "Julia 1.1"
    此函数至少需要 Julia 1.1。

