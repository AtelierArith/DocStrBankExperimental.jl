```
Base.hasfastin(T)
```

确定计算 `x ∈ collection` 其中 `collection::T` 是否可以被视为“快速”操作（通常是常数或对数复杂度）。为了方便起见，提供了定义 `hasfastin(x) = hasfastin(typeof(x))`，以便可以传递实例而不是类型。然而，应该为新类型定义接受类型参数的形式。

`hasfastin(T)` 的默认值对于 [`AbstractSet`](@ref)、[`AbstractDict`](@ref) 和 [`AbstractRange`](@ref) 的子类型为 `true`，否则为 `false`。
