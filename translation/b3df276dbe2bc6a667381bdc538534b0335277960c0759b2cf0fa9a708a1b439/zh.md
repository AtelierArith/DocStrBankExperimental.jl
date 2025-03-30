```
Base.isprecompiled(pkg::PkgId; ignore_loaded::Bool=false)
```

返回给定项目中的 PkgId 是否已预编译。

默认情况下，此检查遵循与代码加载相同的方法，涉及当前加载的不同版本的依赖项与预期的依赖项之间的关系。要忽略已加载的模块并像在一个新的 Julia 会话中一样回答，请指定 `ignore_loaded=true`。

!!! compat "Julia 1.10"
    此函数至少需要 Julia 1.10。

