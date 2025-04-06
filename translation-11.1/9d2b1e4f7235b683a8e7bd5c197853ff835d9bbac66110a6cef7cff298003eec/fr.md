# [Missing Values](@id missing)

Julia fournit un support pour représenter les valeurs manquantes dans un sens statistique. Cela concerne les situations où aucune valeur n'est disponible pour une variable dans une observation, mais qu'une valeur valide existe théoriquement. Les valeurs manquantes sont représentées via l'objet [`missing`](@ref), qui est l'instance singleton du type [`Missing`](@ref). `missing` est équivalent à [`NULL` in SQL](https://en.wikipedia.org/wiki/NULL_(SQL)) et [`NA` in R](https://cran.r-project.org/doc/manuals/r-release/R-lang.html#NA-handling), et se comporte comme eux dans la plupart des situations.

## Propagation of Missing Values

Les valeurs `missing` *se propagent* automatiquement lorsqu'elles sont passées à des opérateurs et fonctions mathématiques standard. Pour ces fonctions, l'incertitude concernant la valeur de l'un des opérandes induit une incertitude sur le résultat. En pratique, cela signifie qu'une opération mathématique impliquant une valeur `missing` renvoie généralement `missing` :

```jldoctest
julia> missing + 1
missing

julia> "a" * missing
missing

julia> abs(missing)
missing
```

Puisque `missing` est un objet Julia normal, cette règle de propagation ne fonctionne que pour les fonctions qui ont choisi de mettre en œuvre ce comportement. Cela peut être réalisé en :

  * ajout d'une méthode spécifique définie pour les arguments de type `Missing`,
  * acceptant des arguments de ce type, et les passant à des fonctions qui les propagent (comme les opérateurs mathématiques standard).

Les packages devraient considérer s'il est logique de propager les valeurs manquantes lors de la définition de nouvelles fonctions, et définir les méthodes de manière appropriée si tel est le cas. Passer une valeur `missing` à une fonction qui n'a pas de méthode acceptant des arguments de type `Missing` génère une [`MethodError`](@ref), tout comme pour tout autre type.

Les fonctions qui ne propagent pas les valeurs `manquantes` peuvent être modifiées pour le faire en les enveloppant dans la fonction `passmissing` fournie par le package [Missings.jl](https://github.com/JuliaData/Missings.jl). Par exemple, `f(x)` devient `passmissing(f)(x)`.

## Equality and Comparison Operators

Les opérateurs d'égalité et de comparaison standard suivent la règle de propagation présentée ci-dessus : si l'un des opérandes est `manquant`, le résultat est `manquant`. Voici quelques exemples :

```jldoctest
julia> missing == 1
missing

julia> missing == missing
missing

julia> missing < 1
missing

julia> 2 >= missing
missing
```

En particulier, notez que `missing == missing` renvoie `missing`, donc `==` ne peut pas être utilisé pour tester si une valeur est manquante. Pour tester si `x` est `missing`, utilisez [`ismissing(x)`](@ref).

Les opérateurs de comparaison spéciaux [`isequal`](@ref) et [`===`](@ref) sont des exceptions à la règle de propagation. Ils renverront toujours une valeur `Bool`, même en présence de valeurs `missing`, considérant `missing` comme égal à `missing` et différent de toute autre valeur. Ils peuvent donc être utilisés pour tester si une valeur est `missing` :

```jldoctest
julia> missing === 1
false

julia> isequal(missing, 1)
false

julia> missing === missing
true

julia> isequal(missing, missing)
true
```

L'opérateur [`isless`](@ref) est une autre exception : `missing` est considéré comme supérieur à toute autre valeur. Cet opérateur est utilisé par [`sort!`](@ref), qui place donc les valeurs `missing` après toutes les autres valeurs :

```jldoctest
julia> isless(1, missing)
true

julia> isless(missing, Inf)
false

julia> isless(missing, missing)
false
```

## Logical operators

Les opérateurs logiques (ou booléens) [`|`](@ref), [`&`](@ref) et [`xor`](@ref) sont un cas spécial car ils ne propagent des valeurs `manquantes` que lorsque cela est logiquement nécessaire. Pour ces opérateurs, que le résultat soit incertain ou non dépend de l'opération particulière. Cela suit les règles bien établies de [*three-valued logic*](https://en.wikipedia.org/wiki/Three-valued_logic), qui sont mises en œuvre par exemple par `NULL` en SQL et `NA` en R. Cette définition abstraite correspond à un comportement relativement naturel qui est mieux expliqué par des exemples concrets.

Illustrons ce principe avec l'opérateur logique "ou" [`|`](@ref). Selon les règles de la logique booléenne, si l'un des opérandes est `vrai`, la valeur de l'autre opérande n'a pas d'influence sur le résultat, qui sera toujours `vrai` :

```jldoctest
julia> true | true
true

julia> true | false
true

julia> false | true
true
```

Sur la base de cette observation, nous pouvons conclure que si l'un des opérandes est `true` et l'autre `missing`, nous savons que le résultat est `true` malgré l'incertitude concernant la valeur réelle de l'un des opérandes. Si nous avions pu observer la valeur réelle du deuxième opérande, elle ne pourrait être que `true` ou `false`, et dans les deux cas, le résultat serait `true`. Par conséquent, dans ce cas particulier, l'absence ne se propage *pas* :

```jldoctest
julia> true | missing
true

julia> missing | true
true
```

Au contraire, si l'un des opérandes est `false`, le résultat peut être soit `true` soit `false` en fonction de la valeur de l'autre opérande. Par conséquent, si cet opérande est `missing`, le résultat doit également être `missing` :

```jldoctest
julia> false | true
true

julia> true | false
true

julia> false | false
false

julia> false | missing
missing

julia> missing | false
missing
```

Le comportement de l'opérateur logique "et" [`&`](@ref) est similaire à celui de l'opérateur `|`, avec la différence que l'absence ne se propage pas lorsque l'un des opérandes est `false`. Par exemple, lorsque c'est le cas du premier opérande :

```jldoctest
julia> false & false
false

julia> false & true
false

julia> false & missing
false
```

D'autre part, l'absence se propage lorsque l'un des opérandes est `true`, par exemple le premier :

```jldoctest
julia> true & true
true

julia> true & false
false

julia> true & missing
missing
```

Enfin, l'opérateur logique "ou exclusif" [`xor`](@ref) propage toujours les valeurs `manquantes`, puisque les deux opérandes ont toujours un effet sur le résultat. Notez également que l'opérateur de négation [`!`](@ref) renvoie `manquant` lorsque l'opérande est `manquant`, tout comme d'autres opérateurs unaires.

## Control Flow and Short-Circuiting Operators

Les opérateurs de contrôle de flux, y compris [`if`](@ref), [`while`](@ref) et le [ternary operator](@ref man-conditional-evaluation), `x ? y : z`, ne permettent pas de valeurs manquantes. Cela est dû à l'incertitude quant à savoir si la valeur réelle serait `true` ou `false` si nous pouvions l'observer. Cela implique que nous ne savons pas comment le programme devrait se comporter. Dans ce cas, un [`TypeError`](@ref) est lancé dès qu'une valeur `missing` est rencontrée dans ce contexte :

```jldoctest
julia> if missing
           println("here")
       end
ERROR: TypeError: non-boolean (Missing) used in boolean context
```

Pour la même raison, contrairement aux opérateurs logiques présentés ci-dessus, les opérateurs booléens à court-circuit [`&&`](@ref) et [`||`](@ref) ne permettent pas de valeurs `manquantes` dans des situations où la valeur de l'opérande détermine si l'opérande suivant est évalué ou non. Par exemple :

```jldoctest
julia> missing || false
ERROR: TypeError: non-boolean (Missing) used in boolean context

julia> missing && false
ERROR: TypeError: non-boolean (Missing) used in boolean context

julia> true && missing && false
ERROR: TypeError: non-boolean (Missing) used in boolean context
```

En revanche, aucune erreur n'est générée lorsque le résultat peut être déterminé sans les valeurs `missing`. C'est le cas lorsque le code s'arrête avant d'évaluer l'opérande `missing`, et lorsque l'opérande `missing` est le dernier :

```jldoctest
julia> true && missing
missing

julia> false && missing
false
```

## Arrays With Missing Values

Les tableaux contenant des valeurs manquantes peuvent être créés comme d'autres tableaux :

```jldoctest
julia> [1, missing]
2-element Vector{Union{Missing, Int64}}:
 1
  missing
```

Comme cet exemple le montre, le type d'élément de tels tableaux est `Union{Missing, T}`, avec `T` le type des valeurs non manquantes. Cela reflète le fait que les entrées du tableau peuvent être soit de type `T` (ici, `Int64`), soit de type `Missing`. Ce type de tableau utilise un stockage mémoire efficace équivalent à un `Array{T}` contenant les valeurs réelles combiné avec un `Array{UInt8}` indiquant le type de l'entrée (c'est-à-dire si elle est `Missing` ou `T`).

Les tableaux permettant des valeurs manquantes peuvent être construits avec la syntaxe standard. Utilisez `Array{Union{Missing, T}}(missing, dims)` pour créer des tableaux remplis de valeurs manquantes :

```jldoctest
julia> Array{Union{Missing, String}}(missing, 2, 3)
2×3 Matrix{Union{Missing, String}}:
 missing  missing  missing
 missing  missing  missing
```

!!! note
    Utiliser `undef` ou `similaire` peut actuellement donner un tableau rempli de `manquant`, mais ce n'est pas la bonne façon d'obtenir un tel tableau. Utilisez un constructeur `manquant` comme indiqué ci-dessus à la place.


Un tableau avec un type d'élément permettant des entrées `missing` (par exemple, `Vector{Union{Missing, T}}`) qui ne contient aucune entrée `missing` peut être converti en un type de tableau qui n'autorise pas les entrées `missing` (par exemple, `Vector{T}`) en utilisant [`convert`](@ref). Si le tableau contient des valeurs `missing`, une `MethodError` est levée lors de la conversion :

```jldoctest
julia> x = Union{Missing, String}["a", "b"]
2-element Vector{Union{Missing, String}}:
 "a"
 "b"

julia> convert(Array{String}, x)
2-element Vector{String}:
 "a"
 "b"

julia> y = Union{Missing, String}[missing, "b"]
2-element Vector{Union{Missing, String}}:
 missing
 "b"

julia> convert(Array{String}, y)
ERROR: MethodError: Cannot `convert` an object of type Missing to an object of type String
```

## Skipping Missing Values

Puisque les valeurs `manquantes` se propagent avec les opérateurs mathématiques standard, les fonctions de réduction renvoient `manquant` lorsqu'elles sont appelées sur des tableaux contenant des valeurs manquantes :

```jldoctest
julia> sum([1, missing])
missing
```

Dans cette situation, utilisez la fonction [`skipmissing`](@ref) pour ignorer les valeurs manquantes :

```jldoctest
julia> sum(skipmissing([1, missing]))
1
```

Cette fonction utilitaire renvoie un itérateur qui filtre efficacement les valeurs `manquantes`. Elle peut donc être utilisée avec toute fonction qui prend en charge les itérateurs :

```jldoctest skipmissing
julia> x = skipmissing([3, missing, 2, 1])
skipmissing(Union{Missing, Int64}[3, missing, 2, 1])

julia> maximum(x)
3

julia> sum(x)
6

julia> mapreduce(sqrt, +, x)
4.146264369941973
```

Les objets créés en appelant `skipmissing` sur un tableau peuvent être indexés en utilisant des indices du tableau parent. Les indices correspondant à des valeurs manquantes ne sont pas valides pour ces objets, et une erreur est générée lorsqu'on essaie de les utiliser (ils sont également ignorés par `keys` et `eachindex`) :

```jldoctest skipmissing
julia> x[1]
3

julia> x[2]
ERROR: MissingException: the value at index (2,) is missing
[...]
```

Cela permet aux fonctions qui opèrent sur des indices de fonctionner en combinaison avec `skipmissing`. C'est notamment le cas pour les fonctions de recherche et de localisation. Ces fonctions renvoient des indices valides pour l'objet retourné par `skipmissing`, et ce sont également les indices des entrées correspondantes *dans le tableau parent* :

```jldoctest skipmissing
julia> findall(==(1), x)
1-element Vector{Int64}:
 4

julia> findfirst(!iszero, x)
1

julia> argmax(x)
1
```

Utilisez [`collect`](@ref) pour extraire les valeurs non `missing` et les stocker dans un tableau :

```jldoctest skipmissing
julia> collect(x)
3-element Vector{Int64}:
 3
 2
 1
```

## Logical Operations on Arrays

La logique à trois valeurs décrite ci-dessus pour les opérateurs logiques est également utilisée par les fonctions logiques appliquées aux tableaux. Ainsi, les tests d'égalité des tableaux utilisant l'opérateur [`==`](@ref) renvoient `missing` chaque fois que le résultat ne peut pas être déterminé sans connaître la valeur réelle de l'entrée `missing`. En pratique, cela signifie que `missing` est renvoyé si toutes les valeurs non manquantes des tableaux comparés sont égales, mais qu'un ou les deux tableaux contiennent des valeurs manquantes (possiblement à des positions différentes) :

```jldoctest
julia> [1, missing] == [2, missing]
false

julia> [1, missing] == [1, missing]
missing

julia> [1, 2, missing] == [1, missing, 2]
missing
```

En ce qui concerne les valeurs uniques, utilisez [`isequal`](@ref) pour traiter les valeurs `manquantes` comme égales à d'autres valeurs `manquantes`, mais différentes des valeurs non manquantes :

```jldoctest
julia> isequal([1, missing], [1, missing])
true

julia> isequal([1, 2, missing], [1, missing, 2])
false
```

Les fonctions [`any`](@ref) et [`all`](@ref) suivent également les règles de la logique à trois valeurs. Ainsi, elles retournent `missing` lorsque le résultat ne peut pas être déterminé :

```jldoctest
julia> all([true, missing])
missing

julia> all([false, missing])
false

julia> any([true, missing])
true

julia> any([false, missing])
missing
```
