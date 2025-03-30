```
isdefined(m::Module, s::Symbol, [order::Symbol])
isdefined(object, s::Symbol, [order::Symbol])
isdefined(object, index::Int, [order::Symbol])
```

测试全局变量或对象字段是否已定义。参数可以是一个模块和一个符号，或者一个复合对象和字段名称（作为符号）或索引。可选地，可以为操作定义一个顺序。如果字段被声明为 `@atomic`，则强烈建议该规范与对该位置的存储兼容。否则，如果未声明为 `@atomic`，则如果指定，此参数必须为 `:not_atomic`。

要测试数组元素是否已定义，请使用 [`isassigned`](@ref) 代替。

另请参见 [`@isdefined`](@ref)。

# 示例

```jldoctest
julia> isdefined(Base, :sum)
true

julia> isdefined(Base, :NonExistentMethod)
false

julia> a = 1//2;

julia> isdefined(a, 2)
true

julia> isdefined(a, 3)
false

julia> isdefined(a, :num)
true

julia> isdefined(a, :numerator)
false
```
