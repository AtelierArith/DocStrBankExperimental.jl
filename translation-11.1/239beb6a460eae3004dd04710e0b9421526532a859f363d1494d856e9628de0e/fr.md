```
isnumeric(c::AbstractChar) -> Bool
```

Teste si un caractère est numérique. Un caractère est classé comme numérique s'il appartient à la catégorie générale Unicode Nombre, c'est-à-dire un caractère dont le code de catégorie commence par 'N'.

Notez que cette large catégorie inclut des caractères tels que ¾ et ௰. Utilisez [`isdigit`](@ref) pour vérifier si un caractère est un chiffre décimal entre 0 et 9.

# Exemples

```jldoctest
julia> isnumeric('௰')
true

julia> isnumeric('9')
true

julia> isnumeric('α')
false

julia> isnumeric('❤')
false
```
