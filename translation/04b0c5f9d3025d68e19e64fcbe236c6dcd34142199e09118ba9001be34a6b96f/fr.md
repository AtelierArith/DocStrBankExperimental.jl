```
filter!(f, d::AbstractDict)
```

Met à jour `d`, en supprimant les éléments pour lesquels `f` est `false`. La fonction `f` reçoit des paires `key=>value`.

# Exemples

```jldoctest
julia> d = Dict(1=>"a", 2=>"b", 3=>"c")
Dict{Int64, String} avec 3 entrées :
  2 => "b"
  3 => "c"
  1 => "a"

julia> filter!(p->isodd(p.first), d)
Dict{Int64, String} avec 2 entrées :
  3 => "c"
  1 => "a"
```
