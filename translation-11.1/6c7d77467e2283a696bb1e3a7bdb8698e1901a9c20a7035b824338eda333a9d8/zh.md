```
BigInt(x)
```

创建一个任意精度的整数。`x` 可以是一个 `Int`（或任何可以转换为 `Int` 的东西）。对于这种类型，定义了通常的数学运算符，结果会提升为 [`BigInt`](@ref)。

可以通过 [`parse`](@ref) 从字符串构造实例，或使用 `big` 字符串字面量。

# 示例

```jldoctest
julia> parse(BigInt, "42")
42

julia> big"313"
313

julia> BigInt(10)^19
10000000000000000000
```
