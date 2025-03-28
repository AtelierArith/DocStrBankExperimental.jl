```
WeakRef(x)
```

`w = WeakRef(x)` construit une [référence faible](https://en.wikipedia.org/wiki/Weak_reference) à la valeur Julia `x` : bien que `w` contienne une référence à `x`, cela n'empêche pas `x` d'être collecté par le ramasse-miettes. `w.value` est soit `x` (si `x` n'a pas encore été collecté), soit `nothing` (si `x` a été collecté).

```jldoctest
julia> x = "a string"
"a string"

julia> w = WeakRef(x)
WeakRef("a string")

julia> GC.gc()

julia> w           # une référence est maintenue via `x`
WeakRef("a string")

julia> x = nothing # effacer la référence

julia> GC.gc()

julia> w
WeakRef(nothing)
```
