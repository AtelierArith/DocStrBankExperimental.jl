```
applicable(f, args...) -> Bool
```

确定给定的泛型函数是否有适用于给定参数的方法。

另见 [`hasmethod`](@ref)。

# 示例

```jldoctest
julia> function f(x, y)
           x + y
       end;

julia> applicable(f, 1)
false

julia> applicable(f, 1, 2)
true
```
