```
ceil([T,] x)
ceil(x; digits::Integer= [, base = 10])
ceil(x; sigdigits::Integer= [, base = 10])
```

`ceil(x)` 返回与 `x` 相同类型的最接近的整数值，该值大于或等于 `x`。

`ceil(T, x)` 将结果转换为类型 `T`，如果向上取整的值无法表示为 `T`，则会抛出 `InexactError`。

关键字 `digits`、`sigdigits` 和 `base` 的工作方式与 [`round`](@ref) 相同。

要支持新类型的 `ceil`，请定义 `Base.round(x::NewType, ::RoundingMode{:Up})`。
