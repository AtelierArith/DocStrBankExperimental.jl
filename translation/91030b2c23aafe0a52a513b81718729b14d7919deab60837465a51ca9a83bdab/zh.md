```
factorial(n::Integer)
```

`n` 的阶乘。如果 `n` 是一个 [`Integer`](@ref)，则阶乘作为整数计算（提升到至少 64 位）。请注意，如果 `n` 不小，这可能会导致溢出，但您可以使用 `factorial(big(n))` 来以任意精度精确计算结果。

另见 [`binomial`](@ref)。

# 示例

```jldoctest
julia> factorial(6)
720

julia> factorial(21)
ERROR: OverflowError: 21 is too large to look up in the table; consider using `factorial(big(21))` instead
Stacktrace:
[...]

julia> factorial(big(21))
51090942171709440000
```

# 外部链接

  * [Factorial](https://en.wikipedia.org/wiki/Factorial) 在维基百科上。
