```
partialsort!(v, k; by=identity, lt=isless, rev=false)
```

Trie partiellement le vecteur `v` sur place de sorte que la valeur à l'index `k` (ou plage de valeurs adjacentes si `k` est une plage) se trouve à la position où elle apparaîtrait si le tableau était entièrement trié. Si `k` est un seul index, cette valeur est renvoyée ; si `k` est une plage, un tableau de valeurs à ces indices est renvoyé. Notez que `partialsort!` peut ne pas trier complètement le tableau d'entrée.

Pour les arguments de mot-clé, voir la documentation de [`sort!`](@ref).

# Exemples

```jldoctest
julia> a = [1, 2, 4, 3, 4]
5-element Vector{Int64}:
 1
 2
 4
 3
 4

julia> partialsort!(a, 4)
4

julia> a
5-element Vector{Int64}:
 1
 2
 3
 4
 4

julia> a = [1, 2, 4, 3, 4]
5-element Vector{Int64}:
 1
 2
 4
 3
 4

julia> partialsort!(a, 4, rev=true)
2

julia> a
5-element Vector{Int64}:
 4
 4
 3
 2
 1
```
