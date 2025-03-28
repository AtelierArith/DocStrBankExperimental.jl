```
@something(x...)
```

Kurzschlussversion von [`something`](@ref).

# Beispiele

```jldoctest
julia> f(x) = (println("f($x)"); nothing);

julia> a = 1;

julia> a = @something a f(2) f(3) error("Standardwert für `a` nicht gefunden")
1

julia> b = nothing;

julia> b = @something b f(2) f(3) error("Standardwert für `b` nicht gefunden")
f(2)
f(3)
ERROR: Standardwert für `b` nicht gefunden
[...]

julia> b = @something b f(2) f(3) Some(nothing)
f(2)
f(3)

julia> b === nothing
true
```

!!! compat "Julia 1.7"
    Dieses Makro ist seit Julia 1.7 verfügbar.

