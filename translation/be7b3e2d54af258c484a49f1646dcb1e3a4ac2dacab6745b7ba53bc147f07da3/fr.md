```
isassigned(ref::RefValue) -> Bool
```

Testez si le [`Ref`](@ref) donné est associé à une valeur. Cela est toujours vrai pour un [`Ref`](@ref) d'un objet de type bitstype. Retournez `false` si la référence est indéfinie.

# Exemples

```jldoctest
julia> ref = Ref{Function}()
Base.RefValue{Function}(#undef)

julia> isassigned(ref)
false

julia> ref[] = (foobar(x) = x)
foobar (generic function with 1 method)

julia> isassigned(ref)
true

julia> isassigned(Ref{Int}())
true
```
