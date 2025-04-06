```
AssertionError([msg])
```

La condition affirmée n'a pas été évaluée à `true`. L'argument optionnel `msg` est une chaîne de caractères descriptive d'erreur.

# Exemples

```jldoctest
julia> @assert false "ceci n'est pas vrai"
ERROR: AssertionError: ceci n'est pas vrai
```

`AssertionError` est généralement lancé par [`@assert`](@ref). ```
