```
keepat!(a::Vector, m::AbstractVector{Bool})
keepat!(a::BitVector, m::AbstractVector{Bool})
```

La versión en el lugar de la indexación lógica `a = a[m]`. Es decir, `keepat!(a, m)` en vectores de igual longitud `a` y `m` eliminará todos los elementos de `a` para los cuales `m` en el índice correspondiente es `false`.

# Ejemplos

```jldoctest
julia> a = [:a, :b, :c];

julia> keepat!(a, [true, false, true])
2-element Vector{Symbol}:
 :a
 :c

julia> a
2-element Vector{Symbol}:
 :a
 :c
```
