```
ispunct(c::AbstractChar) -> Bool
```

Teste si un caractère appartient à la catégorie générale Unicode Punctuation, c'est-à-dire un caractère dont le code de catégorie commence par 'P'.

# Exemples

```jldoctest
julia> ispunct('α')
false

julia> ispunct('/')
true

julia> ispunct(';')
true
```
