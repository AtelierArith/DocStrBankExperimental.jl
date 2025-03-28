```
@coalesce(x...)
```

Version à court-circuit de [`coalesce`](@ref).

# Exemples

```jldoctest
julia> f(x) = (println("f($x)"); missing);

julia> a = 1;

julia> a = @coalesce a f(2) f(3) error("`a` est toujours manquant")
1

julia> b = missing;

julia> b = @coalesce b f(2) f(3) error("`b` est toujours manquant")
f(2)
f(3)
ERROR: `b` est toujours manquant
[...]
```

!!! compat "Julia 1.7"
    Ce macro est disponible depuis Julia 1.7.

