```
partialsortperm(v, k; by=identity, lt=isless, rev=false)
```

Gibt eine partielle Permutation `I` des Vektors `v` zurück, sodass `v[I]` Werte einer vollständig sortierten Version von `v` an Index `k` zurückgibt. Wenn `k` ein Bereich ist, wird ein Vektor von Indizes zurückgegeben; wenn `k` eine ganze Zahl ist, wird ein einzelner Index zurückgegeben. Die Reihenfolge wird mit denselben Schlüsselwörtern wie `sort!` angegeben. Die Permutation ist stabil: die Indizes gleichwertiger Elemente erscheinen in aufsteigender Reihenfolge.

Diese Funktion ist äquivalent zu, aber effizienter als, `sortperm(...)[k]` aufzurufen.

# Beispiele

```jldoctest
julia> v = [3, 1, 2, 1];

julia> v[partialsortperm(v, 1)]
1

julia> p = partialsortperm(v, 1:3)
3-element view(::Vector{Int64}, 1:3) with eltype Int64:
 2
 4
 3

julia> v[p]
3-element Vector{Int64}:
 1
 1
 2
```
