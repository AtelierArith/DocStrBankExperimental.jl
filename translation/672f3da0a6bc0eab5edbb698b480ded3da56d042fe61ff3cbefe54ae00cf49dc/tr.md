```
reverseind(v, i)
```

Bir `i` indeksi [`reverse(v)`](@ref) içinde verildiğinde, `v[reverseind(v,i)] == reverse(v)[i]` olacak şekilde `v` içindeki karşılık gelen indeksi döndürün. (Bu, `v`'nin ASCII olmayan karakterler içerdiği durumlarda karmaşık olabilir.)

# Örnekler

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
