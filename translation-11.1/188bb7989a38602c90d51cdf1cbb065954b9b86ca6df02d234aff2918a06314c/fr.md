```
@timev expr
@timev "description" expr
```

Ceci est une version détaillée de la macro `@time`. Elle imprime d'abord les mêmes informations que `@time`, puis tout compteur d'allocation mémoire non nul, et retourne ensuite la valeur de l'expression.

Fournissez éventuellement une chaîne de description à imprimer avant le rapport de temps.

!!! compat "Julia 1.8"
    L'option d'ajouter une description a été introduite dans Julia 1.8.


Voir aussi [`@time`](@ref), [`@timed`](@ref), [`@elapsed`](@ref), [`@allocated`](@ref), et [`@allocations`](@ref).

```julia-repl
julia> x = rand(10,10);

julia> @timev x * x;
  0.546770 seconds (2.20 M allocations: 116.632 MiB, 4.23% gc time, 99.94% compilation time)
elapsed time (ns): 546769547
gc time (ns):      23115606
bytes allocated:   122297811
pool allocs:       2197930
non-pool GC allocs:1327
malloc() calls:    36
realloc() calls:   5
GC pauses:         3

julia> @timev x * x;
  0.000010 seconds (1 allocation: 896 bytes)
elapsed time (ns): 9848
bytes allocated:   896
pool allocs:       1
```
