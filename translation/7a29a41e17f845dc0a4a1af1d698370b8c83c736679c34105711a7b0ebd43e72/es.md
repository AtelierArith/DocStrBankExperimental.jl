```
mean(f, itr)
```

Aplica la función `f` a cada elemento de la colección `itr` y toma la media.

```jldoctest
julia> using Statistics

julia> mean(√, [1, 2, 3])
1.3820881233139908

julia> mean([√1, √2, √3])
1.3820881233139908
```
