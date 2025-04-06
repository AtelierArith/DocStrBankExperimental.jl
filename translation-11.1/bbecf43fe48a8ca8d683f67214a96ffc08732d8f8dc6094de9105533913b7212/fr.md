```
filter(f, d::AbstractDict)
```

Retourne une copie de `d`, en supprimant les éléments pour lesquels `f` est `false`. La fonction `f` reçoit des paires `key=>value`.

# Exemples

```jldoctest
julia> d = Dict(1=>"a", 2=>"b")
Dict{Int64, String} avec 2 entrées :
  2 => "b"
  1 => "a"

julia> filter(p->isodd(p.first), d)
Dict{Int64, String} avec 1 entrée :
  1 => "a"
```
