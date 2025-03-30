```
public
```

`public` 用于模块中，以告诉 Julia 哪些名称是模块的公共 API 的一部分。例如：`public foo` 表示名称 `foo` 是公共的，但在 [`using`](@ref) 模块时并不可用。有关详细信息，请参见 [manual section about modules](@ref modules)。

!!! compat "Julia 1.11"
    public 关键字是在 Julia 1.11 中添加的。在此之前，公共性的概念不够明确。

