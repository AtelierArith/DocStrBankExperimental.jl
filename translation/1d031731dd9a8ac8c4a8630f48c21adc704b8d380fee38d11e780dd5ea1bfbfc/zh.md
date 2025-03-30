```
UndefRefError()
```

该项或字段未在给定对象中定义。

# 示例

```jldoctest
julia> struct MyType
           a::Vector{Int}
           MyType() = new()
       end

julia> A = MyType()
MyType(#undef)

julia> A.a
错误：UndefRefError：访问未定义的引用
堆栈跟踪：
[...]
```
