```
isassigned(ref::RefValue) -> Bool
```

Prueba si el [`Ref`](@ref) dado está asociado con un valor. Esto siempre es cierto para un [`Ref`](@ref) de un objeto de tipo bitstype. Devuelve `false` si la referencia no está definida.

# Ejemplos

```jldoctest
julia> ref = Ref{Function}()
Base.RefValue{Function}(#undef)

julia> isassigned(ref)
false

julia> ref[] = (foobar(x) = x)
foobar (función genérica con 1 método)

julia> isassigned(ref)
true

julia> isassigned(Ref{Int}())
true
```
