```
split(str::AbstractString, dlm; limit::Integer=0, keepempty::Bool=true)
split(str::AbstractString; limit::Integer=0, keepempty::Bool=false)
```

Divise `str` en un tableau de sous-chaînes sur les occurrences du ou des délimiteurs `dlm`. `dlm` peut être n'importe quel des formats autorisés par le premier argument de [`findnext`](@ref) (c'est-à-dire sous forme de chaîne, d'expression régulière ou de fonction), ou comme un seul caractère ou une collection de caractères.

Si `dlm` est omis, il par défaut à [`isspace`](@ref).

Les arguments de mot-clé optionnels sont :

  * `limit` : la taille maximale du résultat. `limit=0` implique aucune limite (par défaut)
  * `keepempty` : si les champs vides doivent être conservés dans le résultat. Par défaut, c'est `false` sans argument `dlm`, `true` avec un argument `dlm`.

Voir aussi [`rsplit`](@ref), [`eachsplit`](@ref).

# Exemples

```jldoctest
julia> a = "Ma.rch"
"Ma.rch"

julia> split(a, ".")
2-element Vector{SubString{String}}:
 "Ma"
 "rch"
```
