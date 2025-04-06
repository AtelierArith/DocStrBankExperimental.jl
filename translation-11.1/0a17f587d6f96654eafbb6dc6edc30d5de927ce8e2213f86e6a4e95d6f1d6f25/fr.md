```
@fastmath expr
```

Exécutez une version transformée de l'expression, qui appelle des fonctions pouvant violer les sémantiques IEEE strictes. Cela permet l'opération la plus rapide possible, mais les résultats sont indéfinis – soyez prudent lorsque vous faites cela, car cela peut changer les résultats numériques.

Cela définit les [drapeaux Fast-Math LLVM](https://llvm.org/docs/LangRef.html#fast-math-flags), et correspond à l'option `-ffast-math` dans clang. Voir [les notes sur les annotations de performance](@ref man-performance-annotations) pour plus de détails.

# Exemples

```jldoctest
julia> @fastmath 1+2
3

julia> @fastmath(sin(3))
0.1411200080598672
```
