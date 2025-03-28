```
unique(f, itr)
```

Devuelve un array que contiene un valor de `itr` para cada valor único producido por `f` aplicado a los elementos de `itr`.

# Ejemplos

```jldoctest
julia> unique(x -> x^2, [1, -1, 3, -3, 4])
3-element Vector{Int64}:
 1
 3
 4
```

Esta funcionalidad también se puede utilizar para extraer los *índices* de las primeras ocurrencias de elementos únicos en un array:

```jldoctest
julia> a = [3.1, 4.2, 5.3, 3.1, 3.1, 3.1, 4.2, 1.7];

julia> i = unique(i -> a[i], eachindex(a))
4-element Vector{Int64}:
 1
 2
 3
 8

julia> a[i]
4-element Vector{Float64}:
 3.1
 4.2
 5.3
 1.7

julia> a[i] == unique(a)
true
```
