```
@big_str str
```

将字符串解析为 [`BigInt`](@ref) 或 [`BigFloat`](@ref)，如果字符串不是有效的数字，则抛出 `ArgumentError`。对于整数，字符串中允许使用 `_` 作为分隔符。

# 示例

```jldoctest
julia> big"123_456"
123456

julia> big"7891.5"
7891.5

julia> big"_"
ERROR: ArgumentError: invalid number format _ for BigInt or BigFloat
[...]
```

!!! warning
    使用 `@big_str` 构造 [`BigFloat`](@ref) 值可能不会产生天真预期的行为：作为一个宏，`@big_str` 遵循全局精度 ([`setprecision`](@ref)) 和舍入模式 ([`setrounding`](@ref)) 设置，这些设置在 *加载时* 确定。因此，像 `() -> precision(big"0.3")` 这样的函数返回一个常量，其值取决于函数定义时的精度值，而**不是**函数调用时的精度值。

