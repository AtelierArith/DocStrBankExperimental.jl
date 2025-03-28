```
thisind(s::AbstractString, i::Integer) -> Int
```

Si `i` est dans les limites de `s`, retourne l'index du début du caractère dont l'unité de code d'encodage `i` fait partie. En d'autres termes, si `i` est le début d'un caractère, retourne `i` ; si `i` n'est pas le début d'un caractère, rembobine jusqu'au début d'un caractère et retourne cet index. Si `i` est égal à 0 ou `ncodeunits(s)+1`, retourne `i`. Dans tous les autres cas, lance `BoundsError`.

# Exemples

```jldoctest
julia> thisind("α", 0)
0

julia> thisind("α", 1)
1

julia> thisind("α", 2)
1

julia> thisind("α", 3)
3

julia> thisind("α", 4)
ERROR: BoundsError: attempt to access 2-codeunit String at index [4]
[...]

julia> thisind("α", -1)
ERROR: BoundsError: attempt to access 2-codeunit String at index [-1]
[...]
```
