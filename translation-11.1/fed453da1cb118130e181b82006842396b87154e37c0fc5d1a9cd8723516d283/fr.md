```
isspace(c::AbstractChar) -> Bool
```

Teste si un caractère est un caractère d'espacement. Inclut les caractères ASCII '\t', '\n', '\v', '\f', '\r' et ' ', le caractère Latin-1 U+0085, et les caractères de la catégorie Unicode Zs.

# Exemples

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
