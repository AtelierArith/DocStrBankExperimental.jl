```
eachrsplit(str::AbstractString, dlm; limit::Integer=0, keepempty::Bool=true)
eachrsplit(str::AbstractString; limit::Integer=0, keepempty::Bool=false)
```

Renvoie un itérateur sur les `SubString`s de `str`, produits lors de la séparation sur le(s) délimiteur(s) `dlm`, et fournis dans l'ordre inverse (de droite à gauche). `dlm` peut être n'importe quel des formats autorisés par le premier argument de [`findprev`](@ref) (c'est-à-dire une chaîne, un seul caractère ou une fonction), ou une collection de caractères.

Si `dlm` est omis, il par défaut à [`isspace`](@ref), et `keepempty` par défaut à `false`.

Les arguments de mot-clé optionnels sont :

  * Si `limit > 0`, l'itérateur séparera au maximum `limit - 1` fois avant de renvoyer le reste de la chaîne non séparé. `limit < 1` implique aucune limite aux séparations (par défaut).
  * `keepempty` : si les champs vides doivent être renvoyés lors de l'itération. La valeur par défaut est `false` sans argument `dlm`, `true` avec un argument `dlm`.

Notez que contrairement à [`split`](@ref), [`rsplit`](@ref) et [`eachsplit`](@ref), cette fonction itère les sous-chaînes de droite à gauche comme elles apparaissent dans l'entrée.

Voir aussi [`eachsplit`](@ref), [`rsplit`](@ref).

!!! compat "Julia 1.11"
    Cette fonction nécessite Julia 1.11 ou une version ultérieure.


# Exemples

```jldoctest
julia> a = "Ma.r.ch";

julia> collect(eachrsplit(a, ".")) == ["ch", "r", "Ma"]
true

julia> collect(eachrsplit(a, "."; limit=2)) == ["ch", "Ma.r"]
true
```
