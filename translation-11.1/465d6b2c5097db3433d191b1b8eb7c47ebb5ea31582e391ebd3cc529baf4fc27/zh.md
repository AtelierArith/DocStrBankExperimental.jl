```
trunc([T,] x)
trunc(x; digits::Integer= [, base = 10])
trunc(x; sigdigits::Integer= [, base = 10])
```

`trunc(x)` 返回与 `x` 相同类型的最接近的整数值，其绝对值小于或等于 `x` 的绝对值。

`trunc(T, x)` 将结果转换为类型 `T`，如果截断值无法表示为 `T`，则抛出 `InexactError`。

关键字 `digits`、`sigdigits` 和 `base` 的工作方式与 [`round`](@ref) 相同。

要支持 `trunc` 用于新类型，请定义 `Base.round(x::NewType, ::RoundingMode{:ToZero})`。

另请参见: [`%`](@ref rem), [`floor`](@ref), [`unsigned`](@ref), [`unsafe_trunc`](@ref)。

# 示例

```jldoctest
julia> trunc(2.22)
2.0

julia> trunc(-2.22, digits=1)
-2.2

julia> trunc(Int, -2.22)
-2
```
