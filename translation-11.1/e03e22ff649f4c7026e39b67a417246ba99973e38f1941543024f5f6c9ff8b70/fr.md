```
rstrip([pred=isspace,] str::AbstractString) -> SubString
rstrip(str::AbstractString, chars) -> SubString
```

Supprime les caractères de fin de `str`, soit ceux spécifiés par `chars`, soit ceux pour lesquels la fonction `pred` renvoie `true`.

Le comportement par défaut est de supprimer les espaces et les délimiteurs de fin : voir [`isspace`](@ref) pour des détails précis.

L'argument optionnel `chars` spécifie quels caractères supprimer : il peut s'agir d'un seul caractère, ou d'un vecteur ou d'un ensemble de caractères.

Voir aussi [`strip`](@ref) et [`lstrip`](@ref).

# Exemples

```jldoctest
julia> a = rpad("March", 20)
"March               "

julia> rstrip(a)
"March"
```
