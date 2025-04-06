```
fieldtype(T, name::Symbol | index::Int)
```

确定复合数据类型 `T` 中字段（由名称或索引指定）的声明类型。

# 示例

```jldoctest
julia> struct Foo
           x::Int64
           y::String
       end

julia> fieldtype(Foo, :x)
Int64

julia> fieldtype(Foo, 2)
String
```
