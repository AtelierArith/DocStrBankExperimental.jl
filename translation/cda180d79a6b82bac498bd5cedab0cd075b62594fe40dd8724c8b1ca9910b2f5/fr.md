```
Tuple{Types...}
```

Un tuple est un conteneur de longueur fixe qui peut contenir des valeurs de différents types, mais ne peut pas être modifié (il est immuable). Les valeurs peuvent être accessibles par indexation. Les littéraux de tuple sont écrits avec des virgules et des parenthèses :

```jldoctest
julia> (1, 1+1)
(1, 2)

julia> (1,)
(1,)

julia> x = (0.0, "hello", 6*7)
(0.0, "hello", 42)

julia> x[2]
"hello"

julia> typeof(x)
Tuple{Float64, String, Int64}
```

Un tuple de longueur 1 doit être écrit avec une virgule, `(1,)`, car `(1)` serait simplement une valeur entre parenthèses. `()` représente le tuple vide (de longueur 0).

Un tuple peut être construit à partir d'un itérateur en utilisant un type `Tuple` comme constructeur :

```jldoctest
julia> Tuple(["a", 1])
("a", 1)

julia> Tuple{String, Float64}(["a", 1])
("a", 1.0)
```

Les types de tuple sont covariants dans leurs paramètres : `Tuple{Int}` est un sous-type de `Tuple{Any}`. Par conséquent, `Tuple{Any}` est considéré comme un type abstrait, et les types de tuple ne sont concrets que si leurs paramètres le sont. Les tuples n'ont pas de noms de champ ; les champs ne sont accessibles que par index. Les types de tuple peuvent avoir n'importe quel nombre de paramètres.

Voir la section du manuel sur [Tuple Types](@ref).

Voir aussi [`Vararg`](@ref), [`NTuple`](@ref), [`ntuple`](@ref), [`tuple`](@ref), [`NamedTuple`](@ref).
