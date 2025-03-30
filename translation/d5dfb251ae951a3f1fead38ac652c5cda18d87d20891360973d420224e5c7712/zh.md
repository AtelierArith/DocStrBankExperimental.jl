```
@coalesce(x...)
```

[`coalesce`](@ref) 的短路版本。

# 示例

```jldoctest
julia> f(x) = (println("f($x)"); missing);

julia> a = 1;

julia> a = @coalesce a f(2) f(3) error("`a` 仍然是缺失的")
1

julia> b = missing;

julia> b = @coalesce b f(2) f(3) error("`b` 仍然是缺失的")
f(2)
f(3)
ERROR: `b` 仍然是缺失的
[...]
```

!!! compat "Julia 1.7"
    此宏自 Julia 1.7 起可用。

