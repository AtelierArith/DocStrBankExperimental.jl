```
continue
```

Sauter le reste de l'itération actuelle de la boucle.

# Exemples

```jldoctest
julia> for i = 1:6
           iseven(i) && continue
           println(i)
       end
1
3
5
```
