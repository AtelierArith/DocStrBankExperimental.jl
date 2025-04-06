```
supertypes(T::Type)
```

Devuelve una tupla `(T, ..., Any)` de `T` y todos sus supertipos, según lo determinado por llamadas sucesivas a la función [`supertype`](@ref), listados en orden de `<:` y terminados por `Any`.

Véase también [`subtypes`](@ref).

# Ejemplos

```jldoctest
julia> supertypes(Int)
(Int64, Signed, Integer, Real, Number, Any)
```
