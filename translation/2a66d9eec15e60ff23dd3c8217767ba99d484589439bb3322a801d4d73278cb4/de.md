```
graphemes(s::AbstractString, m:n) -> SubString
```

Gibt einen [`SubString`](@ref) von `s` zurück, der aus den `m`-ten bis `n`-ten Graphemen des Strings `s` besteht, wobei das zweite Argument `m:n` ein ganzzahliger [`AbstractUnitRange`](@ref) ist.

Locker gesprochen entspricht dies den `m:n`-ten vom Benutzer wahrgenommenen "Zeichen" im String. Zum Beispiel:

```jldoctest
julia> s = graphemes("exposé", 3:6)
"posé"

julia> collect(s)
5-element Vector{Char}:
 'p': ASCII/Unicode U+0070 (Kategorie Ll: Buchstabe, Kleinbuchstabe)
 'o': ASCII/Unicode U+006F (Kategorie Ll: Buchstabe, Kleinbuchstabe)
 's': ASCII/Unicode U+0073 (Kategorie Ll: Buchstabe, Kleinbuchstabe)
 'e': ASCII/Unicode U+0065 (Kategorie Ll: Buchstabe, Kleinbuchstabe)
 '́': Unicode U+0301 (Kategorie Mn: Zeichen, nicht trennend)
```

Dies besteht aus den 3. bis *7.* Codepunkten ([`Char`](@ref)s) in `"exposé"`, da das Graphem `"é"` tatsächlich *zwei* Unicode-Codepunkte (ein `'e'` gefolgt von einem akzentuierenden Kombinationszeichen U+0301) ist.

Da das Finden von Graphemgrenzen eine Iteration über den Inhalt des Strings erfordert, benötigt die Funktion `graphemes(s, m:n)` eine Zeit, die proportional zur Länge des Strings (Anzahl der Codepunkte) vor dem Ende des Substrings ist.

!!! compat "Julia 1.9"
    Das Argument `m:n` von `graphemes` erfordert Julia 1.9.


```
