```
flatten(iter)
```

Étant donné un itérateur qui produit des itérateurs, renvoie un itérateur qui produit les éléments de ces itérateurs. En d'autres termes, les éléments de l'itérateur d'argument sont concaténés.

# Exemples

```jldoctest
julia> collect(Iterators.flatten((1:2, 8:9)))
4-element Vector{Int64}:
 1
 2
 8
 9

julia> [(x,y) for x in 0:1 for y in 'a':'c']  # collecte des générateurs impliquant Iterators.flatten
6-element Vector{Tuple{Int64, Char}}:
 (0, 'a')
 (0, 'b')
 (0, 'c')
 (1, 'a')
 (1, 'b')
 (1, 'c')
```
