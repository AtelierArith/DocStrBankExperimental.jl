```
cbrt(x::Real)
```

Retourne la racine cubique de `x`, c'est-à-dire $x^{1/3}$. Les valeurs négatives sont acceptées (retournant la racine réelle négative lorsque $x < 0$).

L'opérateur préfixe `∛` est équivalent à `cbrt`.

# Exemples

```jldoctest
julia> cbrt(big(27))
3.0

julia> cbrt(big(-27))
-3.0
```
