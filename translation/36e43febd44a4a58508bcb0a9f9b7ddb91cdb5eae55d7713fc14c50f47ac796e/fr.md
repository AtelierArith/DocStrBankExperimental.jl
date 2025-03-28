```
step(r)
```

Obtenez la taille du pas d'un objet [`AbstractRange`](@ref).

# Exemples

```jldoctest
julia> step(1:10)
1

julia> step(1:2:10)
2

julia> step(2.5:0.3:10.9)
0.3

julia> step(range(2.5, stop=10.9, length=85))
0.1
```
