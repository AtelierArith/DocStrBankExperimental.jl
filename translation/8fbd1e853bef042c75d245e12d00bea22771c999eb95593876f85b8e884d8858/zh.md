```
fieldtypes(T::Type)
```

复合数据类型 `T` 中所有字段的声明类型，作为一个元组。

!!! compat "Julia 1.1"
    此函数至少需要 Julia 1.1。


# 示例

```jldoctest
julia> struct Foo
           x::Int64
           y::String
       end

julia> fieldtypes(Foo)
(Int64, String)
```
