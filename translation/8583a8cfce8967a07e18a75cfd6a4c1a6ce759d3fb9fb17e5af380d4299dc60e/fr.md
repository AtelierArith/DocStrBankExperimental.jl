```
merge(a::NamedTuple, iterable)
```

Interprète un itérable de paires clé-valeur comme un tuple nommé, et effectue une fusion.

```jldoctest
julia> merge((a=1, b=2, c=3), [:b=>4, :d=>5])
(a = 1, b = 4, c = 3, d = 5)
```
