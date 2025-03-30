```
^(x, y)
```

指数运算符。

如果 `x` 和 `y` 是整数，结果可能会溢出。要以科学计数法输入数字，请使用 [`Float64`](@ref) 字面量，例如 `1.2e3` 而不是 `1.2 * 10^3`。

如果 `y` 是 `Int` 字面量（例如 `x^2` 中的 `2` 或 `x^-3` 中的 `-3`），Julia 代码 `x^y` 会被编译器转换为 `Base.literal_pow(^, x, Val(y))`，以便在指数值上进行编译时特化。（作为默认回退，我们有 `Base.literal_pow(^, x, Val(y)) = ^(x,y)`，通常 `^ == Base.^`，除非在调用命名空间中定义了 `^`。）如果 `y` 是负整数字面量，则 `Base.literal_pow` 默认将操作转换为 `inv(x)^-y`，其中 `-y` 是正数。

另请参见 [`exp2`](@ref)，[`<<`](@ref)。

# 示例

```jldoctest
julia> 3^5
243

julia> 3^-1  # 使用 Base.literal_pow
0.3333333333333333

julia> p = -1;

julia> 3^p
ERROR: DomainError with -1:
Cannot raise an integer x to a negative power -1.
[...]

julia> 3.0^p
0.3333333333333333

julia> 10^19 > 0  # 整数溢出
false

julia> big(10)^19 == 1e19
true
```
