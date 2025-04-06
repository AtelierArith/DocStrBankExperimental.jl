```
hasfield(T::Type, name::Symbol)
```

返回一个布尔值，指示 `T` 是否将 `name` 作为其自身字段之一。

另请参见 [`fieldnames`](@ref), [`fieldcount`](@ref), [`hasproperty`](@ref).

!!! compat "Julia 1.2"
    此函数至少需要 Julia 1.2。


# 示例

```jldoctest
julia> struct Foo
            bar::Int
       end

julia> hasfield(Foo, :bar)
true

julia> hasfield(Foo, :x)
false
```
