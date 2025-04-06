```
reverseind(v, i)
```

Gegeben einen Index `i` in [`reverse(v)`](@ref), gib den entsprechenden Index in `v` zurück, sodass `v[reverseind(v,i)] == reverse(v)[i]`. (Dies kann nicht trivial sein, wenn `v` nicht-ASCII-Zeichen enthält.)

# Beispiele

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
