```
mktempdir(f::Function, parent=tempdir(); prefix="jl_")
```

将函数 `f` 应用到 [`mktempdir(parent; prefix)`](@ref) 的结果，并在完成后删除临时目录及其所有内容。

另见: [`mktemp`](@ref), [`mkdir`](@ref).

!!! compat "Julia 1.2"
    `prefix` 关键字参数是在 Julia 1.2 中添加的。

