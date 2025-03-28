```
lstrip([pred=isspace,] str::AbstractString) -> SubString
lstrip(str::AbstractString, chars) -> SubString
```

Supprime les caractères de tête de `str`, soit ceux spécifiés par `chars`, soit ceux pour lesquels la fonction `pred` retourne `true`.

Le comportement par défaut est de supprimer les espaces et les délimiteurs de tête : voir [`isspace`](@ref) pour des détails précis.

L'argument optionnel `chars` spécifie quels caractères supprimer : il peut s'agir d'un seul caractère, ou d'un vecteur ou d'un ensemble de caractères.

Voir aussi [`strip`](@ref) et [`rstrip`](@ref).

# Exemples

```jldoctest
julia> a = lpad("March", 20)
"               March"

julia> lstrip(a)
"March"
```
