```
reverseind(v, i)
```

Étant donné un index `i` dans [`reverse(v)`](@ref), renvoie l'index correspondant dans `v` de sorte que `v[reverseind(v,i)] == reverse(v)[i]`. (Cela peut être non trivial dans les cas où `v` contient des caractères non-ASCII.)

# Exemples

```jldoctest
julia> s = "Julia🚀"
"Julia🚀"

julia> r = reverse(s)
"🚀ailuJ"

julia> for i in eachindex(s)
           print(r[reverseind(r, i)])
       end
Julia🚀
```
