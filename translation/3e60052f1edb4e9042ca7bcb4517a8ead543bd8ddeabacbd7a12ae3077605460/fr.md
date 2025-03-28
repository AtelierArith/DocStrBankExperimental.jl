```
filter!(f, a)
```

Met à jour la collection `a`, en supprimant les éléments pour lesquels `f` est `false`. La fonction `f` reçoit un argument.

# Exemples

```jldoctest
julia> filter!(isodd, Vector(1:10))
5-element Vector{Int64}:
 1
 3
 5
 7
 9
```
