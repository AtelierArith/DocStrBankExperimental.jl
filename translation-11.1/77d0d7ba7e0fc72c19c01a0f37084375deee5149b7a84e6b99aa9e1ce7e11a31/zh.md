```
可变结构体
```

`mutable struct` 类似于 [`struct`](@ref)，但额外允许在构造后设置类型的字段。

可变结构体的单个字段可以标记为 `const` 以使其不可变：

```julia
mutable struct Baz
    a::Int
    const b::Float64
end
```

!!! compat "Julia 1.8"
    可变结构体字段的 `const` 关键字需要至少 Julia 1.8。


有关更多信息，请参阅手册中的 [复合类型](@ref) 部分。
