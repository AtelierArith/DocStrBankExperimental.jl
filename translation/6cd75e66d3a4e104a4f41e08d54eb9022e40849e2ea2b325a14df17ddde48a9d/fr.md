```
rpad(s, n::Integer, p::Union{AbstractChar,AbstractString}=' ') -> String
```

Transformez `s` en chaîne et complétez la chaîne résultante à droite avec `p` pour qu'elle fasse `n` caractères (dans [`textwidth`](@ref)) de long. Si `s` fait déjà `n` caractères de long, une chaîne égale est renvoyée. Complétez par des espaces par défaut.

# Exemples

```jldoctest
julia> rpad("March", 20)
"March               "
```

!!! compat "Julia 1.7"
    Dans Julia 1.7, cette fonction a été modifiée pour utiliser `textwidth` plutôt qu'un compte de caractères brut (codepoint).

