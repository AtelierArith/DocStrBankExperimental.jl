```
mean(f, itr)
```

Appliquez la fonction `f` à chaque élément de la collection `itr` et prenez la moyenne.

```jldoctest
julia> using Statistics

julia> mean(√, [1, 2, 3])
1.3820881233139908

julia> mean([√1, √2, √3])
1.3820881233139908
```
