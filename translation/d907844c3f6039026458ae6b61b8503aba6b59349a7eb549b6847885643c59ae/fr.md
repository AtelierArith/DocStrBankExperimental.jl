```
NamedTuple
```

Les `NamedTuple` sont, comme leur nom l'indique, des [`Tuple`](@ref) nommés. C'est-à-dire qu'ils constituent une collection de valeurs semblable à un tuple, où chaque entrée a un nom unique, représenté sous la forme d'un [`Symbol`](@ref). Comme les `Tuple`, les `NamedTuple` sont immuables ; ni les noms ni les valeurs ne peuvent être modifiés sur place après leur construction.

Un tuple nommé peut être créé comme un littéral de tuple avec des clés, par exemple `(a=1, b=2)`, ou comme un littéral de tuple avec un point-virgule après la parenthèse d'ouverture, par exemple `(; a=1, b=2)` (cette forme accepte également des noms générés par programme comme décrit ci-dessous), ou en utilisant un type `NamedTuple` comme constructeur, par exemple `NamedTuple{(:a, :b)}((1,2))`.

L'accès à la valeur associée à un nom dans un tuple nommé peut se faire en utilisant la syntaxe d'accès aux champs, par exemple `x.a`, ou en utilisant [`getindex`](@ref), par exemple `x[:a]` ou `x[(:a, :b)]`. Un tuple des noms peut être obtenu en utilisant [`keys`](@ref), et un tuple des valeurs peut être obtenu en utilisant [`values`](@ref).

!!! note
    L'itération sur les `NamedTuple` produit les *valeurs* sans les noms. (Voir l'exemple ci-dessous.) Pour itérer sur les paires nom-valeur, utilisez la fonction [`pairs`](@ref).


Le macro [`@NamedTuple`](@ref) peut être utilisé pour déclarer commodément des types `NamedTuple`.

# Exemples

```jldoctest
julia> x = (a=1, b=2)
(a = 1, b = 2)

julia> x.a
1

julia> x[:a]
1

julia> x[(:a,)]
(a = 1,)

julia> keys(x)
(:a, :b)

julia> values(x)
(1, 2)

julia> collect(x)
2-element Vector{Int64}:
 1
 2

julia> collect(pairs(x))
2-element Vector{Pair{Symbol, Int64}}:
 :a => 1
 :b => 2
```

De la même manière que l'on peut définir des arguments de mots-clés par programme, un tuple nommé peut être créé en donnant des paires `name::Symbol => value` après un point-virgule à l'intérieur d'un littéral de tuple. Cette syntaxe et la syntaxe `name=value` peuvent être mélangées :

```jldoctest
julia> (; :a => 1, :b => 2, c=3)
(a = 1, b = 2, c = 3)
```

Les paires nom-valeur peuvent également être fournies en splattant un tuple nommé ou tout itérateur qui produit des collections à deux valeurs contenant chacune un symbole comme première valeur :

```jldoctest
julia> keys = (:a, :b, :c); values = (1, 2, 3);

julia> NamedTuple{keys}(values)
(a = 1, b = 2, c = 3)

julia> (; (keys .=> values)...)
(a = 1, b = 2, c = 3)

julia> nt1 = (a=1, b=2);

julia> nt2 = (c=3, d=4);

julia> (; nt1..., nt2..., b=20) # le dernier b écrase la valeur de nt1
(a = 1, b = 20, c = 3, d = 4)

julia> (; zip(keys, values)...) # zip produit des tuples tels que (:a, 1)
(a = 1, b = 2, c = 3)
```

Comme pour les arguments de mots-clés, les identifiants et les expressions à point indiquent des noms :

```jldoctest
julia> x = 0
0

julia> t = (; x)
(x = 0,)

julia> (; t.x)
(x = 0,)
```

!!! compat "Julia 1.5"
    Les noms implicites provenant des identifiants et des expressions à point sont disponibles depuis Julia 1.5.


!!! compat "Julia 1.7"
    L'utilisation des méthodes `getindex` avec plusieurs `Symbol`s est disponible depuis Julia 1.7.

