```
collect(type_d_element, collection)
```

Renvoie un `Array` avec le type d'élément donné de tous les éléments d'une collection ou d'un itérable. Le résultat a la même forme et le même nombre de dimensions que `collection`.

# Exemples

```jldoctest
julia> collect(Float64, 1:2:5)
3-element Vector{Float64}:
 1.0
 3.0
 5.0
```
