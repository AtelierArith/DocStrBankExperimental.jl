```
reverseind(v, i)
```

Dada un índice `i` en [`reverse(v)`](@ref), devuelve el índice correspondiente en `v` de modo que `v[reverseind(v,i)] == reverse(v)[i]`. (Esto puede ser no trivial en casos donde `v` contiene caracteres no ASCII.)

# Ejemplos

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
