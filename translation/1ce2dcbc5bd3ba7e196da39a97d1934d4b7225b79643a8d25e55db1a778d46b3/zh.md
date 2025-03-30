```
@isdefined s -> Bool
```

测试变量 `s` 是否在当前作用域中定义。

另请参见 [`isdefined`](@ref) 以获取字段属性，以及 [`isassigned`](@ref) 以获取数组索引或 [`haskey`](@ref) 以获取其他映射。

# 示例

```jldoctest
julia> @isdefined newvar
false

julia> newvar = 1
1

julia> @isdefined newvar
true

julia> function f()
           println(@isdefined x)
           x = 3
           println(@isdefined x)
       end
f (generic function with 1 method)

julia> f()
false
true
```
