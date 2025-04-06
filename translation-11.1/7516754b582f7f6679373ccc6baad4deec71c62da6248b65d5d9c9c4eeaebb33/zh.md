```
LoadError(file::AbstractString, line::Int, error)
```

在 [`include`](@ref Base.include)、[`require`](@ref Base.require) 或 [`using`](@ref) 文件时发生错误。错误的具体信息应在 `.error` 字段中可用。

!!! compat "Julia 1.7"
    从 Julia 1.7 开始，`@macroexpand`、`@macroexpand1` 和 `macroexpand` 不再发出 LoadErrors。

