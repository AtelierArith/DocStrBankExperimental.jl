```
isspace(c::AbstractChar) -> Bool
```

Überprüft, ob ein Zeichen ein beliebiges Leerzeichen ist. Beinhaltet ASCII-Zeichen '\t', '\n', '\v', '\f', '\r' und ' ', das Latin-1-Zeichen U+0085 sowie Zeichen in der Unicode-Kategorie Zs.

# Beispiele

```jldoctest
julia> isspace('\n')
true

julia> isspace('\r')
true

julia> isspace(' ')
true

julia> isspace('\x20')
true
```
