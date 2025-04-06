```
Iterators.accumulate(f, itr; [init])
```

Étant donné une fonction à 2 arguments `f` et un itérateur `itr`, renvoie un nouvel itérateur qui applique successivement `f` à la valeur précédente et au prochain élément de `itr`.

C'est effectivement une version paresseuse de [`Base.accumulate`](@ref).

!!! compat "Julia 1.5"
    L'argument clé `init` a été ajouté dans Julia 1.5.


# Exemples

```jldoctest
julia> a = Iterators.accumulate(+, [1,2,3,4]);

julia> foreach(println, a)
1
3
6
10

julia> b = Iterators.accumulate(/, (2, 5, 2, 5); init = 100);

julia> collect(b)
4-element Vector{Float64}:
 50.0
 10.0
  5.0
  1.0
```
