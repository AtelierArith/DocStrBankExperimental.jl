```
eachsplit(str::AbstractString, dlm; limit::Integer=0, keepempty::Bool=true)
eachsplit(str::AbstractString; limit::Integer=0, keepempty::Bool=false)
```

Divise `str` sur les occurrences du ou des délimiteurs `dlm` et renvoie un itérateur sur les sous-chaînes. `dlm` peut être n'importe quel des formats autorisés par le premier argument de [`findnext`](@ref) (c'est-à-dire sous forme de chaîne, d'expression régulière ou de fonction), ou comme un seul caractère ou une collection de caractères.

Si `dlm` est omis, il par défaut à [`isspace`](@ref).

Les arguments optionnels sont :

  * `limit` : la taille maximale du résultat. `limit=0` implique pas de maximum (par défaut)
  * `keepempty` : si les champs vides doivent être conservés dans le résultat. Par défaut, c'est `false` sans argument `dlm`, `true` avec un argument `dlm`.

Voir aussi [`split`](@ref).

!!! compat "Julia 1.8"
    La fonction `eachsplit` nécessite au moins Julia 1.8.


# Exemples

```jldoctest
julia> a = "Ma.rch"
"Ma.rch"

julia> b = eachsplit(a, ".")
Base.SplitIterator{String, String}("Ma.rch", ".", 0, true)

julia> collect(b)
2-element Vector{SubString{String}}:
 "Ma"
 "rch"
```
