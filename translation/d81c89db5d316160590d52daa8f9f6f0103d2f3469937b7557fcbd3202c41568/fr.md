```
strip([pred=isspace,] str::AbstractString) -> SubString
strip(str::AbstractString, chars) -> SubString
```

Supprime les caractères en tête et en fin de `str`, soit ceux spécifiés par `chars`, soit ceux pour lesquels la fonction `pred` retourne `true`.

Le comportement par défaut est de supprimer les espaces et délimiteurs en tête et en fin : voir [`isspace`](@ref) pour des détails précis.

L'argument optionnel `chars` spécifie quels caractères supprimer : il peut s'agir d'un seul caractère, d'un vecteur ou d'un ensemble de caractères.

Voir aussi [`lstrip`](@ref) et [`rstrip`](@ref).

!!! compat "Julia 1.2"
    La méthode qui accepte une fonction prédicat nécessite Julia 1.2 ou une version ultérieure.


# Exemples

```jldoctest
julia> strip("{3, 5}\n", ['{', '}', '\n'])
"3, 5"
```
