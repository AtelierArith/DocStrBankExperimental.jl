```
unescape_string(str::AbstractString, keep = ())::AbstractString
unescape_string(io, s::AbstractString, keep = ())::Nothing
```

Allgemeines Unescaping von traditionellen C- und Unicode-Escape-Sequenzen. Die erste Form gibt den entkommenen String zurück, die zweite gibt das Ergebnis an `io` aus. Das Argument `keep` gibt eine Sammlung von Zeichen an, die (neben Rückwärtsschrägstrichen) so belassen werden sollen, wie sie sind.

Die folgenden Escape-Sequenzen werden erkannt:

  * Entkommener Rückwärtsschrägstrich (`\\`)
  * Entkommener Doppelanführungszeichen (`\"`)
  * Standard C-Escape-Sequenzen (`\a`, `\b`, `\t`, `\n`, `\v`, `\f`, `\r`, `\e`)
  * Unicode BMP-Codepunkte (`\u` mit 1-4 nachfolgenden hexadezimalen Ziffern)
  * Alle Unicode-Codepunkte (`\U` mit 1-8 nachfolgenden hexadezimalen Ziffern; max Wert = 0010ffff)
  * Hexadezimale Bytes (`\x` mit 1-2 nachfolgenden hexadezimalen Ziffern)
  * Oktale Bytes (`\` mit 1-3 nachfolgenden oktalen Ziffern)

Siehe auch [`escape_string`](@ref).

# Beispiele

```jldoctest
julia> unescape_string("aaa\\nbbb") # C-Escape-Sequenz
"aaa\nbbb"

julia> unescape_string("\\u03c0") # unicode
"π"

julia> unescape_string("\\101") # oktal
"A"

julia> unescape_string("aaa \\g \\n", ['g']) # Verwendung des `keep`-Arguments
"aaa \\g \n"
```
