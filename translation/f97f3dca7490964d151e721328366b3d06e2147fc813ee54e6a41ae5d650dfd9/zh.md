```
floor([T,] x)
floor(x; digits::Integer= [, base = 10])
floor(x; sigdigits::Integer= [, base = 10])
```

`floor(x)` 返回与 `x` 相同类型的最接近的整数值，该值小于或等于 `x`。

`floor(T, x)` 将结果转换为类型 `T`，如果向下取整的值无法表示为 `T`，则会抛出 `InexactError`。

关键字 `digits`、`sigdigits` 和 `base` 的工作方式与 [`round`](@ref) 相同。

要支持新类型的 `floor`，请定义 `Base.round(x::NewType, ::RoundingMode{:Down})`。
