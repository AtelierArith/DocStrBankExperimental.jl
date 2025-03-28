```
mean(f, itr)
```

Wenden Sie die Funktion `f` auf jedes Element der Sammlung `itr` an und berechnen Sie den Durchschnitt.

```jldoctest
julia> using Statistics

julia> mean(√, [1, 2, 3])
1.3820881233139908

julia> mean([√1, √2, √3])
1.3820881233139908
```
