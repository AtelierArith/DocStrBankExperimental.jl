```
pkgversion(m::Module)
```

返回导入模块 `m` 的包的版本，如果 `m` 不是从包中导入的，或者从没有设置版本字段的包中导入，则返回 `nothing`。

版本在包加载期间从包的 Project.toml 中读取。

要获取导入当前模块的包的版本，可以使用形式 `pkgversion(@__MODULE__)`。

!!! compat "Julia 1.9"
    此函数是在 Julia 1.9 中引入的。

