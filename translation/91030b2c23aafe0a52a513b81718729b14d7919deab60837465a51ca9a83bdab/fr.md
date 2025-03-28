```
factorial(n::Integer)
```

Factorielle de `n`. Si `n` est un [`Integer`](@ref), la factorielle est calculée comme un entier (promu à au moins 64 bits). Notez que cela peut provoquer un dépassement si `n` n'est pas petit, mais vous pouvez utiliser `factorial(big(n))` pour calculer le résultat exactement en précision arbitraire.

Voir aussi [`binomial`](@ref).

# Exemples

```jldoctest
julia> factorial(6)
720

julia> factorial(21)
ERROR: OverflowError: 21 est trop grand pour être recherché dans la table ; envisagez d'utiliser `factorial(big(21))` à la place
Stacktrace:
[...]

julia> factorial(big(21))
51090942171709440000
```

# Liens externes

  * [Factorielle](https://en.wikipedia.org/wiki/Factorial) sur Wikipedia.

```
