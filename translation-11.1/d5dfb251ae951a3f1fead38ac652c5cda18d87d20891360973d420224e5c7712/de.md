```
@coalesce(x...)
```

Kurzschlussversion von [`coalesce`](@ref).

# Beispiele

```jldoctest
julia> f(x) = (println("f($x)"); missing);

julia> a = 1;

julia> a = @coalesce a f(2) f(3) error("`a` ist immer noch fehlend")
1

julia> b = missing;

julia> b = @coalesce b f(2) f(3) error("`b` ist immer noch fehlend")
f(2)
f(3)
ERROR: `b` ist immer noch fehlend
[...]
```

!!! compat "Julia 1.7"
    Dieses Makro ist seit Julia 1.7 verfügbar.

