```
foreach(f, c...) -> Rien
```

Appelle la fonction `f` sur chaque élément de l'itérable `c`. Pour plusieurs arguments itérables, `f` est appelé élément par élément, et l'itération s'arrête lorsque n'importe quel itérateur est terminé.

`foreach` doit être utilisé au lieu de [`map`](@ref) lorsque les résultats de `f` ne sont pas nécessaires, par exemple dans `foreach(println, array)`.

# Exemples

```jldoctest
julia> tri = 1:3:7; res = Int[];

julia> foreach(x -> push!(res, x^2), tri)

julia> res
3-element Vector{Int64}:
  1
 16
 49

julia> foreach((x, y) -> println(x, " avec ", y), tri, 'a':'z')
1 avec a
4 avec b
7 avec c
```
