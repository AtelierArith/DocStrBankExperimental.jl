```
@kwdef typedef
```

Ceci est une macro d'aide qui définit automatiquement un constructeur basé sur des mots-clés pour le type déclaré dans l'expression `typedef`, qui doit être une expression `struct` ou `mutable struct`. L'argument par défaut est fourni en déclarant des champs sous la forme `field::T = default` ou `field = default`. Si aucun défaut n'est fourni, alors l'argument de mot-clé devient un argument de mot-clé requis dans le constructeur de type résultant.

Des constructeurs internes peuvent toujours être définis, mais au moins un doit accepter des arguments sous la même forme que le constructeur interne par défaut (c'est-à-dire un argument positionnel par champ) afin de fonctionner correctement avec le constructeur externe basé sur des mots-clés.

!!! compat "Julia 1.1"
    `Base.@kwdef` pour les structs paramétriques, et les structs avec des supertypes nécessite au moins Julia 1.1.


!!! compat "Julia 1.9"
    Cette macro est exportée depuis Julia 1.9.


# Exemples

```jldoctest
julia> @kwdef struct Foo
           a::Int = 1         # défaut spécifié
           b::String          # mot-clé requis
       end
Foo

julia> Foo(b="hi")
Foo(1, "hi")

julia> Foo()
ERROR: UndefKeywordError: argument de mot-clé `b` non assigné
Stacktrace:
[...]
```
