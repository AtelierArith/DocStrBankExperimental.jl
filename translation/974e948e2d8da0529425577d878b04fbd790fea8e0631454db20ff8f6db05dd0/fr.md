```
gcd(x, y...)
```

Plus grand commun diviseur (ou zéro si tous les arguments sont zéro). Les arguments peuvent être des nombres entiers et rationnels.

!!! compat "Julia 1.4"
    Les arguments rationnels nécessitent Julia 1.4 ou version ultérieure.


# Exemples

```jldoctest
julia> gcd(6, 9)
3

julia> gcd(6, -9)
3

julia> gcd(6, 0)
6

julia> gcd(0, 0)
0

julia> gcd(1//3, 2//3)
1//3

julia> gcd(1//3, -2//3)
1//3

julia> gcd(1//3, 2)
1//3

julia> gcd(0, 0, 10, 15)
5
```
