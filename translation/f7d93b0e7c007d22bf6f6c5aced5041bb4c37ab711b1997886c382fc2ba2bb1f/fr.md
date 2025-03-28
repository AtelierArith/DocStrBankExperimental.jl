```
nextind(str::AbstractString, i::Integer, n::Integer=1) -> Int
```

  * Cas `n == 1`

    Si `i` est dans les limites de `s`, retourne l'index du début du caractère dont l'encodage commence après l'index `i`. En d'autres termes, si `i` est le début d'un caractère, retourne le début du caractère suivant ; si `i` n'est pas le début d'un caractère, avance jusqu'au début d'un caractère et retourne cet index. Si `i` est égal à `0`, retourne `1`. Si `i` est dans les limites mais supérieur ou égal à `lastindex(str)`, retourne `ncodeunits(str)+1`. Sinon, lance `BoundsError`.
  * Cas `n > 1`

    Comporte comme l'application de `n` fois `nextind` pour `n==1`. La seule différence est que si `n` est si grand que l'application de `nextind` atteindrait `ncodeunits(str)+1`, alors chaque itération restante augmente la valeur retournée de `1`. Cela signifie que dans ce cas, `nextind` peut retourner une valeur supérieure à `ncodeunits(str)+1`.
  * Cas `n == 0`

    Retourne `i` uniquement si `i` est un index valide dans `s` ou est égal à `0`. Sinon, `StringIndexError` ou `BoundsError` est lancé.

# Exemples

```jldoctest
julia> nextind("α", 0)
1

julia> nextind("α", 1)
3

julia> nextind("α", 3)
ERROR: BoundsError: attempt to access 2-codeunit String at index [3]
[...]

julia> nextind("α", 0, 2)
3

julia> nextind("α", 1, 2)
4
```
