```
Sys.isdragonfly([os])
```

用于测试操作系统是否是 DragonFly BSD 的派生版本的谓词。请参阅 [Handling Operating System Variation](@ref) 中的文档。

!!! note
    不要与 `Sys.isbsd()` 混淆，后者在 DragonFly 以及其他基于 BSD 的系统上均为 `true`。`Sys.isdragonfly()` 仅指 DragonFly。


!!! compat "Julia 1.1"
    此函数至少需要 Julia 1.1。

