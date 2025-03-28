```
escape_string(str::AbstractString[, esc]; keep = ())::AbstractString
escape_string(io, str::AbstractString[, esc]; keep = ())::Nothing
```

Échappement général des séquences d'échappement traditionnelles C et Unicode. La première forme renvoie la chaîne échappée, la seconde imprime le résultat dans `io`.

Les barres obliques inverses (`\`) sont échappées avec une double barre oblique inverse (`"\\"`). Les caractères non imprimables sont échappés soit avec leurs codes d'échappement C standard, `"\0"` pour NUL (si non ambigu), point de code unicode (`"\u"` préfixe) ou hexadécimal (`"\x"` préfixe).

L'argument optionnel `esc` spécifie tout caractère supplémentaire qui doit également être échappé par un backslash (`"` est également échappé par défaut dans la première forme).

L'argument `keep` spécifie une collection de caractères qui doivent être conservés tels quels. Remarquez que `esc` a la priorité ici.

Voir aussi [`unescape_string`](@ref) pour l'opération inverse.

!!! compat "Julia 1.7"
    L'argument `keep` est disponible depuis Julia 1.7.


# Exemples

```jldoctest
julia> escape_string("aaa\nbbb")
"aaa\\nbbb"

julia> escape_string("aaa\nbbb"; keep = '\n')
"aaa\nbbb"

julia> escape_string("\xfe\xff") # utf-8 invalide
"\\xfe\\xff"

julia> escape_string(string('\u2135','\0')) # non ambigu
"ℵ\\0"

julia> escape_string(string('\u2135','\0','0')) # \0 serait ambigu
"ℵ\\x000"
```
