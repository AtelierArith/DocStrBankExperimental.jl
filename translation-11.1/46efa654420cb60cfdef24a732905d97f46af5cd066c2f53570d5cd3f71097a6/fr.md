```
splat(f)
```

Équivalent à

```julia
    my_splat(f) = args->f(args...)
```

c'est-à-dire qu'étant donné une fonction, cela renvoie une nouvelle fonction qui prend un argument et le décompose dans la fonction originale. Cela est utile comme adaptateur pour passer une fonction à plusieurs arguments dans un contexte qui attend un seul argument, mais passe un tuple comme cet argument unique.

# Exemples

```jldoctest
julia> map(splat(+), zip(1:3,4:6))
3-element Vector{Int64}:
 5
 7
 9

julia> my_add = splat(+)
splat(+)

julia> my_add((1,2,3))
6
```
