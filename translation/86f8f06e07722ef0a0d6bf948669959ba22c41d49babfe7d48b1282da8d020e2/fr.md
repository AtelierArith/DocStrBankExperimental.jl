```
argmax(f, domaine)
```

Retourne une valeur `x` de `domaine` pour laquelle `f(x)` est maximisé. S'il y a plusieurs valeurs maximales pour `f(x)`, alors la première sera trouvée.

`domaine` doit être un itérable non vide.

Les valeurs sont comparées avec `isless`.

!!! compat "Julia 1.7"
    Cette méthode nécessite Julia 1.7 ou une version ultérieure.


Voir aussi [`argmin`](@ref), [`findmax`](@ref).

# Exemples

```jldoctest
julia> argmax(abs, -10:5)
-10

julia> argmax(cos, 0:π/2:2π)
0.0
```
