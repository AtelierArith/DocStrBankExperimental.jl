```
prevind(str::AbstractString, i::Integer, n::Integer=1) -> Int
```

  * Cas `n == 1`

    Si `i` est dans les limites de `s`, retourne l'index du début du caractère dont l'encodage commence avant l'index `i`. En d'autres termes, si `i` est le début d'un caractère, retourne le début du caractère précédent ; si `i` n'est pas le début d'un caractère, rembobine jusqu'au début d'un caractère et retourne cet index. Si `i` est égal à `1`, retourne `0`. Si `i` est égal à `ncodeunits(str)+1`, retourne `lastindex(str)`. Sinon, lance `BoundsError`.
  * Cas `n > 1`

    Comporte comme l'application de `n` fois `prevind` pour `n==1`. La seule différence est que si `n` est si grand que l'application de `prevind` atteindrait `0`, alors chaque itération restante diminue la valeur retournée de `1`. Cela signifie que dans ce cas, `prevind` peut retourner une valeur négative.
  * Cas `n == 0`

    Retourne `i` uniquement si `i` est un index valide dans `str` ou est égal à `ncodeunits(str)+1`. Sinon, `StringIndexError` ou `BoundsError` est lancé.

# Exemples

```jldoctest
julia> prevind("α", 3)
1

julia> prevind("α", 1)
0

julia> prevind("α", 0)
ERROR: BoundsError: attempt to access 2-codeunit String at index [0]
[...]

julia> prevind("α", 2, 2)
0

julia> prevind("α", 2, 3)
-1
```
