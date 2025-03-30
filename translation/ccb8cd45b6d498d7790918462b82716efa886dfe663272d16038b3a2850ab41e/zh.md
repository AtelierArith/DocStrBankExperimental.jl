```
names(x::Module; all::Bool = false, imported::Bool = false)
```

获取一个 `Module` 的公共名称向量，排除已弃用的名称。如果 `all` 为真，则列表还包括模块中定义的非公共名称、已弃用的名称和编译器生成的名称。如果 `imported` 为真，则还包括从其他模块显式导入的名称。名称按排序顺序返回。

作为特例，所有在 `Main` 中定义的名称被视为“公共”，因为在 `Main` 中显式标记名称为公共并不是惯用的做法。

!!! note
    `sym ∈ names(SomeModule)` 并不 *意味着* `isdefined(SomeModule, sym)`。`names` 将返回标记为 `public` 或 `export` 的符号，即使它们未在模块中定义。


另请参见: [`Base.isexported`](@ref), [`Base.ispublic`](@ref), [`Base.@locals`](@ref), [`@__MODULE__`](@ref).
