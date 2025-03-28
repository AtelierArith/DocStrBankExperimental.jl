```
unescape_string(str::AbstractString, keep = ())::AbstractString
unescape_string(io, s::AbstractString, keep = ())::Nothing
```

Déséchappement général des séquences d'échappement traditionnelles C et Unicode. La première forme renvoie la chaîne déséchappée, la seconde imprime le résultat dans `io`. L'argument `keep` spécifie une collection de caractères qui (avec les barres obliques inverses) doivent être conservés tels quels.

Les séquences d'échappement suivantes sont reconnues :

  * Barre oblique inverse échappée (`\\`)
  * Guillemets doubles échappés (`\"`)
  * Séquences d'échappement C standard (`\a`, `\b`, `\t`, `\n`, `\v`, `\f`, `\r`, `\e`)
  * Points de code Unicode BMP (`\u` avec 1-4 chiffres hexadécimaux à la fin)
  * Tous les points de code Unicode (`\U` avec 1-8 chiffres hexadécimaux à la fin ; valeur max = 0010ffff)
  * Octets hexadécimaux (`\x` avec 1-2 chiffres hexadécimaux à la fin)
  * Octets octaux (`\` avec 1-3 chiffres octaux à la fin)

Voir aussi [`escape_string`](@ref).

# Exemples

```jldoctest
julia> unescape_string("aaa\\nbbb") # séquence d'échappement C
"aaa\nbbb"

julia> unescape_string("\\u03c0") # unicode
"π"

julia> unescape_string("\\101") # octal
"A"

julia> unescape_string("aaa \\g \\n", ['g']) # utilisation de l'argument `keep`
"aaa \\g \n"
```
