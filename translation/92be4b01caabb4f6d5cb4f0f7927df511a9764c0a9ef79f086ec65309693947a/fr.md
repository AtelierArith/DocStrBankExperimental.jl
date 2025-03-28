```
pop!(collection, key[, default])
```

Supprime et retourne le mappage pour `key` s'il existe dans `collection`, sinon retourne `default`, ou lance une erreur si `default` n'est pas spécifié.

# Exemples

```jldoctest
julia> d = Dict("a"=>1, "b"=>2, "c"=>3);

julia> pop!(d, "a")
1

julia> pop!(d, "d")
ERROR: KeyError: key "d" not found
Stacktrace:
[...]

julia> pop!(d, "e", 4)
4
```
