```
a ? b : c
```

Forme courte pour les conditionnels ; se lit "si `a`, évaluer `b` sinon évaluer `c`". Également connu sous le nom de [opérateur ternaire](https://en.wikipedia.org/wiki/%3F:).

Cette syntaxe est équivalente à `if a; b else c end`, mais est souvent utilisée pour mettre en avant la valeur `b`-ou-`c` qui est utilisée comme partie d'une expression plus grande, plutôt que les effets secondaires que l'évaluation de `b` ou `c` peut avoir.

Voir la section du manuel sur [flux de contrôle](@ref man-conditional-evaluation) pour plus de détails.

# Exemples

```jldoctest
julia> x = 1; y = 2;

julia> x > y ? println("x est plus grand") : println("x n'est pas plus grand")
x n'est pas plus grand

julia> x > y ? "x est plus grand" : x == y ? "x et y sont égaux" : "y est plus grand"
"y est plus grand"
```
