```
@coalesce(x...)
```

Versión de cortocircuito de [`coalesce`](@ref).

# Ejemplos

```jldoctest
julia> f(x) = (println("f($x)"); missing);

julia> a = 1;

julia> a = @coalesce a f(2) f(3) error("`a` sigue siendo missing")
1

julia> b = missing;

julia> b = @coalesce b f(2) f(3) error("`b` sigue siendo missing")
f(2)
f(3)
ERROR: `b` sigue siendo missing
[...]
```

!!! compat "Julia 1.7"
    Este macro está disponible a partir de Julia 1.7.

