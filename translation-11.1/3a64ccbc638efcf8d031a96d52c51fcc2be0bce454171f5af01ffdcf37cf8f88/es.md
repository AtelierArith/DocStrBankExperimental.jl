```
@something(x...)
```

Versión de cortocircuito de [`something`](@ref).

# Ejemplos

```jldoctest
julia> f(x) = (println("f($x)"); nothing);

julia> a = 1;

julia> a = @something a f(2) f(3) error("No se puede encontrar un valor predeterminado para `a`")
1

julia> b = nothing;

julia> b = @something b f(2) f(3) error("No se puede encontrar un valor predeterminado para `b`")
f(2)
f(3)
ERROR: No se puede encontrar un valor predeterminado para `b`
[...]

julia> b = @something b f(2) f(3) Some(nothing)
f(2)
f(3)

julia> b === nothing
true
```

!!! compat "Julia 1.7"
    Este macro está disponible a partir de Julia 1.7.

