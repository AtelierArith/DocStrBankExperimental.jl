```
IndexStyle(A)
IndexStyle(typeof(A))
```

`IndexStyle` 指定了数组 `A` 的“原生索引风格”。当你定义一个新的 [`AbstractArray`](@ref) 类型时，你可以选择实现线性索引（使用 [`IndexLinear`](@ref)）或笛卡尔索引。如果你决定只实现线性索引，那么你必须为你的数组类型设置这个特性：

```
Base.IndexStyle(::Type{<:MyArray}) = IndexLinear()
```

默认值是 [`IndexCartesian()`](@ref)。

Julia 的内部索引机制将自动（并且隐式地）将所有索引操作重新计算为首选风格。这允许用户使用任何索引风格访问你的数组元素，即使没有提供显式的方法。

如果你为你的 `AbstractArray` 定义了两种索引风格，这个特性可以用来选择性能最优的索引风格。一些方法会检查其输入上的这个特性，并根据最有效的访问模式调度到不同的算法。特别是，[`eachindex`](@ref) 创建一个迭代器，其类型取决于这个特性的设置。
