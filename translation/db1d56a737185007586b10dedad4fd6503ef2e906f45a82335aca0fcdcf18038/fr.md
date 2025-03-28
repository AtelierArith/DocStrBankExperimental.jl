```
dot(x, y)
x ⋅ y
```

Calculez le produit scalaire entre deux vecteurs. Pour les vecteurs complexes, le premier vecteur est conjugué.

`dot` fonctionne également sur des objets itérables arbitraires, y compris des tableaux de n'importe quelle dimension, tant que `dot` est défini sur les éléments.

`dot` est sémantiquement équivalent à `sum(dot(vx,vy) for (vx,vy) in zip(x, y))`, avec la restriction supplémentaire que les arguments doivent avoir des longueurs égales.

`x ⋅ y` (où `⋅` peut être tapé en complétant par tabulation `\cdot` dans le REPL) est un synonyme de `dot(x, y)`.

# Exemples

```jldoctest
julia> dot([1; 1], [2; 3])
5

julia> dot([im; im], [1; 1])
0 - 2im

julia> dot(1:5, 2:6)
70

julia> x = fill(2., (5,5));

julia> y = fill(3., (5,5));

julia> dot(x, y)
150.0
```
