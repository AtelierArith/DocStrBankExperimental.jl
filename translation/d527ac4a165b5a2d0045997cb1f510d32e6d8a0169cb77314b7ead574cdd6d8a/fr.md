```
AbstractDict{K, V}
```

Supertype pour les types similaires à des dictionnaires avec des clés de type `K` et des valeurs de type `V`. [`Dict`](@ref), [`IdDict`](@ref) et d'autres types sont des sous-types de celui-ci. Un `AbstractDict{K, V}` devrait être un itérateur de `Pair{K, V}`.
