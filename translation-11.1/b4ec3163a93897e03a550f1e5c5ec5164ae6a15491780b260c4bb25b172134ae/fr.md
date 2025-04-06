```
broadcast(f, As...)
```

Diffuser la fonction `f` sur les tableaux, tuples, collections, [`Ref`](@ref)s et/ou scalaires `As`.

Le broadcasting applique la fonction `f` sur les éléments des arguments de conteneur et les scalaires eux-mêmes dans `As`. Les dimensions singleton et manquantes sont étendues pour correspondre aux étendues des autres arguments en répétant virtuellement la valeur. Par défaut, seuls un nombre limité de types sont considérés comme des scalaires, y compris les `Number`s, `String`s, `Symbol`s, `Type`s, `Function`s et quelques singleton courants comme [`missing`](@ref) et [`nothing`](@ref). Tous les autres arguments sont itérés ou indexés élément par élément.

Le type de conteneur résultant est établi par les règles suivantes :

  * Si tous les arguments sont des scalaires ou des tableaux à zéro dimension, il retourne un scalaire non enveloppé.
  * Si au moins un argument est un tuple et que tous les autres sont des scalaires ou des tableaux à zéro dimension, il retourne un tuple.
  * Toutes les autres combinaisons d'arguments par défaut retournent un `Array`, mais les types de conteneurs personnalisés peuvent définir leur propre implémentation et des règles de promotion pour personnaliser le résultat lorsqu'ils apparaissent comme arguments.

Une syntaxe spéciale existe pour le broadcasting : `f.(args...)` est équivalent à `broadcast(f, args...)`, et les appels imbriqués `f.(g.(args...))` sont fusionnés en une seule boucle de broadcasting.

# Exemples

```jldoctest
julia> A = [1, 2, 3, 4, 5]
5-element Vector{Int64}:
 1
 2
 3
 4
 5

julia> B = [1 2; 3 4; 5 6; 7 8; 9 10]
5×2 Matrix{Int64}:
 1   2
 3   4
 5   6
 7   8
 9  10

julia> broadcast(+, A, B)
5×2 Matrix{Int64}:
  2   3
  5   6
  8   9
 11  12
 14  15

julia> parse.(Int, ["1", "2"])
2-element Vector{Int64}:
 1
 2

julia> abs.((1, -2))
(1, 2)

julia> broadcast(+, 1.0, (0, -2.0))
(1.0, -1.0)

julia> (+).([[0,2], [1,3]], Ref{Vector{Int}}([1,-1]))
2-element Vector{Vector{Int64}}:
 [1, 1]
 [2, 2]

julia> string.(("one","two","three","four"), ": ", 1:4)
4-element Vector{String}:
 "one: 1"
 "two: 2"
 "three: 3"
 "four: 4"

```
