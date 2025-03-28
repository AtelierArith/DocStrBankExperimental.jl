```
lpad(s, n::Integer, p::Union{AbstractChar,AbstractString}=' ') -> String
```

Convertir `s` en chaîne et ajouter des caractères `p` à gauche de la chaîne résultante pour qu'elle fasse `n` caractères de long (dans [`textwidth`](@ref)). Si `s` fait déjà `n` caractères de long, une chaîne égale est renvoyée. Par défaut, le remplissage se fait avec des espaces.

# Exemples

```jldoctest
julia> lpad("March", 10)
"     March"
```

!!! compat "Julia 1.7"
    Dans Julia 1.7, cette fonction a été modifiée pour utiliser `textwidth` plutôt qu'un compte de caractères brut (codepoint).

