```
string(xs...)
```

使用[`print`](@ref)函数从任何值创建一个字符串。

`string` 通常不应该直接定义。相反，定义一个方法 `print(io::IO, x::MyType)`。如果某种类型的 `string(x)` 需要高效，那么添加一个方法到 `string` 并定义 `print(io::IO, x::MyType) = print(io, string(x))` 以确保函数的一致性是有意义的。

另请参见：[`String`](@ref), [`repr`](@ref), [`sprint`](@ref), [`show`](@ref @show)。

# 示例

```jldoctest
julia> string("a", 1, true)
"a1true"
```
