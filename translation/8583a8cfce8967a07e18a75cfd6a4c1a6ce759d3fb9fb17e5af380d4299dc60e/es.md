```
merge(a::NamedTuple, iterable)
```

Interpreta un iterable de pares clave-valor como un tuple nombrado y realiza una fusión.

```jldoctest
julia> merge((a=1, b=2, c=3), [:b=>4, :d=>5])
(a = 1, b = 4, c = 3, d = 5)
```
