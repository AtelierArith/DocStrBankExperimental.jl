```
complex(r, [i])
```

Convertir des nombres réels ou des tableaux en complexes. `i` est par défaut égal à zéro.

# Exemples

```jldoctest
julia> complex(7)
7 + 0im

julia> complex([1, 2, 3])
3-element Vector{Complex{Int64}}:
 1 + 0im
 2 + 0im
 3 + 0im
```
