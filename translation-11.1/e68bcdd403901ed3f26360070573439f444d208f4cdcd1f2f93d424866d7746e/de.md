```
complex(r, [i])
```

Konvertiert reelle Zahlen oder Arrays in komplexe Zahlen. `i` ist standardmäßig null.

# Beispiele

```jldoctest
julia> complex(7)
7 + 0im

julia> complex([1, 2, 3])
3-element Vector{Complex{Int64}}:
 1 + 0im
 2 + 0im
 3 + 0im
```
