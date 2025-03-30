```
@something(x...)
```

[`something`](@ref) 的短路版本。

# 示例

```jldoctest
julia> f(x) = (println("f($x)"); nothing);

julia> a = 1;

julia> a = @something a f(2) f(3) error("无法找到 `a` 的默认值")
1

julia> b = nothing;

julia> b = @something b f(2) f(3) error("无法找到 `b` 的默认值")
f(2)
f(3)
错误: 无法找到 `b` 的默认值
[...]

julia> b = @something b f(2) f(3) Some(nothing)
f(2)
f(3)

julia> b === nothing
true
```

!!! compat "Julia 1.7"
    此宏自 Julia 1.7 起可用。

