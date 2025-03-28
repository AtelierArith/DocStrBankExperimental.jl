```
DomainError(val)
DomainError(val, msg)
```

L'argument `val` d'une fonction ou d'un constructeur est en dehors du domaine valide.

# Exemples

```jldoctest
julia> sqrt(-1)
ERROR: DomainError with -1.0:
sqrt a été appelé avec un argument réel négatif mais ne renverra un résultat complexe que s'il est appelé avec un argument complexe. Essayez sqrt(Complex(x)).
Stacktrace:
[...]
```
