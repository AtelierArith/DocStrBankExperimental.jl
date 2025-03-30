```
eigvals!(A::Union{SymTridiagonal, Hermitian, Symmetric}, irange::UnitRange) -> values
```

与 [`eigvals`](@ref) 相同，但通过覆盖输入 `A` 来节省空间，而不是创建副本。`irange` 是要搜索的特征值 *索引* 的范围 - 例如，从第 2 个到第 8 个特征值。
