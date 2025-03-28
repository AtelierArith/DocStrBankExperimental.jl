```
escape_string(str::AbstractString[, esc]; keep = ())::AbstractString
escape_string(io, str::AbstractString[, esc]; keep = ())::Nothing
```

Allgemeines Escaping von traditionellen C- und Unicode-Escape-Sequenzen. Die erste Form gibt den escaped String zurück, die zweite gibt das Ergebnis an `io` aus.

Backslashes (`\`) werden mit einem doppelten Backslash (`"\\"`) escaped. Nicht druckbare Zeichen werden entweder mit ihren standardmäßigen C-Escape-Codes escaped, `"\0"` für NUL (wenn eindeutig), Unicode-Codepunkt (`"\u"`-Präfix) oder hex (`"\x"`-Präfix).

Das optionale Argument `esc` gibt an, welche zusätzlichen Zeichen ebenfalls mit einem vorangestellten Backslash escaped werden sollen (`"` wird auch standardmäßig in der ersten Form escaped).

Das Argument `keep` gibt eine Sammlung von Zeichen an, die so belassen werden sollen, wie sie sind. Beachten Sie, dass `esc` hier Vorrang hat.

Siehe auch [`unescape_string`](@ref) für die umgekehrte Operation.

!!! compat "Julia 1.7"
    Das Argument `keep` ist seit Julia 1.7 verfügbar.


# Beispiele

```jldoctest
julia> escape_string("aaa\nbbb")
"aaa\\nbbb"

julia> escape_string("aaa\nbbb"; keep = '\n')
"aaa\nbbb"

julia> escape_string("\xfe\xff") # ungültiges utf-8
"\\xfe\\xff"

julia> escape_string(string('\u2135','\0')) # eindeutig
"ℵ\\0"

julia> escape_string(string('\u2135','\0','0')) # \0 wäre mehrdeutig
"ℵ\\x000"
```
