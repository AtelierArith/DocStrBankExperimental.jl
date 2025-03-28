```
Val(c)
```

Retourne `Val{c}()`, qui ne contient aucune donnée d'exécution. Des types comme celui-ci peuvent être utilisés pour passer l'information entre les fonctions à travers la valeur `c`, qui doit être une valeur `isbits` ou un `Symbol`. L'intention de cette construction est de pouvoir dispatcher sur des constantes directement (au moment de la compilation) sans avoir à tester la valeur de la constante à l'exécution.

# Exemples

```jldoctest
julia> f(::Val{true}) = "Good"
f (generic function with 1 method)

julia> f(::Val{false}) = "Bad"
f (generic function with 2 methods)

julia> f(Val(true))
"Good"
```
