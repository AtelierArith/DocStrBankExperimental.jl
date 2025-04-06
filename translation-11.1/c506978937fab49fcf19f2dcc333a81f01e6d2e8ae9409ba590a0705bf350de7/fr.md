```
argmin(f, domaine)
```

Retourne une valeur `x` de `domaine` pour laquelle `f(x)` est minimisé. S'il y a plusieurs valeurs minimales pour `f(x)`, alors la première sera trouvée.

`domaine` doit être un itérable non vide.

`NaN` est considéré comme inférieur à toutes les autres valeurs sauf `missing`.

!!! compat "Julia 1.7"
    Cette méthode nécessite Julia 1.7 ou une version ultérieure.


Voir aussi [`argmax`](@ref), [`findmin`](@ref).

# Exemples

```jldoctest
julia> argmin(sign, -10:5)
-10

julia> argmin(x -> -x^3 + x^2 - 10, -5:5)
5

julia> argmin(acos, 0:0.1:1)
1.0
```
