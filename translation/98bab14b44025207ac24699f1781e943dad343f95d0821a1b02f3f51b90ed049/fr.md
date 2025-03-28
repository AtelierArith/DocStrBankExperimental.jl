# Methods

Rappelez-vous de [Functions](@ref man-functions) qu'une fonction est un objet qui associe un tuple d'arguments à une valeur de retour, ou lance une exception si aucune valeur appropriée ne peut être retournée. Il est courant que la même fonction ou opération conceptuelle soit implémentée de manière très différente pour différents types d'arguments : ajouter deux entiers est très différent d'ajouter deux nombres à virgule flottante, qui sont tous deux distincts d'ajouter un entier à un nombre à virgule flottante. Malgré leurs différences d'implémentation, ces opérations relèvent toutes du concept général d'"addition". En conséquence, en Julia, ces comportements appartiennent tous à un seul objet : la fonction `+`.

Pour faciliter l'utilisation de nombreuses implémentations différentes du même concept de manière fluide, les fonctions n'ont pas besoin d'être définies toutes en même temps, mais peuvent plutôt être définies par morceaux en fournissant des comportements spécifiques pour certaines combinaisons de types et de nombres d'arguments. Une définition d'un comportement possible pour une fonction est appelée une *méthode*. Jusqu'à présent, nous n'avons présenté que des exemples de fonctions définies avec une seule méthode, applicable à tous les types d'arguments. Cependant, les signatures des définitions de méthodes peuvent être annotées pour indiquer les types d'arguments en plus de leur nombre, et plus d'une seule définition de méthode peut être fournie. Lorsqu'une fonction est appliquée à un tuple particulier d'arguments, la méthode la plus spécifique applicable à ces arguments est appliquée. Ainsi, le comportement global d'une fonction est un patchwork des comportements de ses différentes définitions de méthode. Si le patchwork est bien conçu, même si les implémentations des méthodes peuvent être très différentes, le comportement extérieur de la fonction apparaîtra fluide et cohérent.

Le choix de la méthode à exécuter lorsqu'une fonction est appliquée s'appelle *dispatch*. Julia permet au processus de dispatch de choisir laquelle des méthodes d'une fonction appeler en fonction du nombre d'arguments donnés et des types de tous les arguments de la fonction. Cela diffère des langages orientés objet traditionnels, où le dispatch se produit uniquement en fonction du premier argument, qui a souvent une syntaxe d'argument spéciale et est parfois implicite plutôt qu'écrit explicitement comme un argument. [^1] Utiliser tous les arguments d'une fonction pour choisir quelle méthode doit être invoquée, plutôt que seulement le premier, est connu sous le nom de [multiple dispatch](https://en.wikipedia.org/wiki/Multiple_dispatch). Le dispatch multiple est particulièrement utile pour le code mathématique, où il n'a guère de sens de considérer que les opérations "appartiennent" à un argument plus qu'à un autre : l'opération d'addition dans `x + y` appartient-elle à `x` plus qu'à `y` ? L'implémentation d'un opérateur mathématique dépend généralement des types de tous ses arguments. Même au-delà des opérations mathématiques, cependant, le dispatch multiple s'avère être un paradigme puissant et pratique pour structurer et organiser des programmes.

[^1]: In C++ or Java, for example, in a method call like `obj.meth(arg1,arg2)`, the object obj "receives" the method call and is implicitly passed to the method via the `this` keyword, rather than as an explicit method argument. When the current `this` object is the receiver of a method call, it can be omitted altogether, writing just `meth(arg1,arg2)`, with `this` implied as the receiving object.

!!! note
    Tous les exemples de ce chapitre supposent que vous définissez des méthodes pour une fonction dans le *même* module. Si vous souhaitez ajouter des méthodes à une fonction dans un *autre* module, vous devez `importer` celui-ci ou utiliser le nom qualifié avec les noms de module. Voir la section sur [namespace management](@ref namespace-management).


## Defining Methods

Jusqu'à présent, nous avons, dans nos exemples, défini uniquement des fonctions avec une seule méthode ayant des types d'arguments non contraints. Ces fonctions se comportent exactement comme elles le feraient dans des langages dynamiquement typés traditionnels. Néanmoins, nous avons utilisé le dispatch multiple et les méthodes presque continuellement sans en être conscients : toutes les fonctions et opérateurs standard de Julia, comme la fonction `+` mentionnée précédemment, ont de nombreuses méthodes définissant leur comportement sur diverses combinaisons possibles de types et de nombres d'arguments.

Lors de la définition d'une fonction, on peut optionnellement contraindre les types de paramètres auxquels elle s'applique, en utilisant l'opérateur d'assertion de type `::`, introduit dans la section sur [Composite Types](@ref) :

```jldoctest fofxy
julia> f(x::Float64, y::Float64) = 2x + y
f (generic function with 1 method)
```

Cette définition de fonction s'applique uniquement aux appels où `x` et `y` sont tous deux des valeurs de type [`Float64`](@ref) :

```jldoctest fofxy
julia> f(2.0, 3.0)
7.0
```

L'application à d'autres types d'arguments entraînera un [`MethodError`](@ref) :

```jldoctest fofxy
julia> f(2.0, 3)
ERROR: MethodError: no method matching f(::Float64, ::Int64)
The function `f` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  f(::Float64, !Matched::Float64)
   @ Main none:1

Stacktrace:
[...]

julia> f(Float32(2.0), 3.0)
ERROR: MethodError: no method matching f(::Float32, ::Float64)
The function `f` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  f(!Matched::Float64, ::Float64)
   @ Main none:1

Stacktrace:
[...]

julia> f(2.0, "3.0")
ERROR: MethodError: no method matching f(::Float64, ::String)
The function `f` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  f(::Float64, !Matched::Float64)
   @ Main none:1

Stacktrace:
[...]

julia> f("2.0", "3.0")
ERROR: MethodError: no method matching f(::String, ::String)
The function `f` exists, but no method is defined for this combination of argument types.
```

Comme vous pouvez le voir, les arguments doivent être précisément de type [`Float64`](@ref). D'autres types numériques, tels que les entiers ou les valeurs flottantes 32 bits, ne sont pas automatiquement convertis en flottants 64 bits, ni les chaînes analysées comme des nombres. Parce que `Float64` est un type concret et que les types concrets ne peuvent pas être sous-classés en Julia, une telle définition ne peut être appliquée qu'aux arguments qui sont exactement de type `Float64`. Il peut cependant souvent être utile d'écrire des méthodes plus générales où les types de paramètres déclarés sont abstraits :

```jldoctest fofxy
julia> f(x::Number, y::Number) = 2x - y
f (generic function with 2 methods)

julia> f(2.0, 3)
1.0
```

Cette définition de méthode s'applique à toute paire d'arguments qui sont des instances de [`Number`](@ref). Ils n'ont pas besoin d'être du même type, tant qu'ils sont chacun des valeurs numériques. Le problème de la gestion des types numériques disparates est délégué aux opérations arithmétiques dans l'expression `2x - y`.

Pour définir une fonction avec plusieurs méthodes, il suffit de définir la fonction plusieurs fois, avec différents nombres et types d'arguments. La première définition de méthode pour une fonction crée l'objet fonction, et les définitions de méthode suivantes ajoutent de nouvelles méthodes à l'objet fonction existant. La définition de méthode la plus spécifique correspondant au nombre et aux types des arguments sera exécutée lorsque la fonction est appliquée. Ainsi, les deux définitions de méthode ci-dessus, prises ensemble, définissent le comportement de `f` pour toutes les paires d'instances du type abstrait `Number` – mais avec un comportement différent spécifique aux paires de valeurs [`Float64`](@ref). Si l'un des arguments est un float 64 bits mais que l'autre ne l'est pas, alors la méthode `f(Float64,Float64)` ne peut pas être appelée et la méthode plus générale `f(Number,Number)` doit être utilisée :

```jldoctest fofxy
julia> f(2.0, 3.0)
7.0

julia> f(2, 3.0)
1.0

julia> f(2.0, 3)
1.0

julia> f(2, 3)
1
```

The `2x + y` definition is only used in the first case, while the `2x - y` definition is used in the others. No automatic casting or conversion of function arguments is ever performed: all conversion in Julia is non-magical and completely explicit. [Conversion and Promotion](@ref conversion-and-promotion), however, shows how clever application of sufficiently advanced technology can be indistinguishable from magic. [^Clarke61]

Pour les valeurs non numériques, et pour moins ou plus de deux arguments, la fonction `f` reste indéfinie, et son application entraînera toujours un [`MethodError`](@ref) :

```jldoctest fofxy
julia> f("foo", 3)
ERROR: MethodError: no method matching f(::String, ::Int64)
The function `f` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  f(!Matched::Number, ::Number)
   @ Main none:1
  f(!Matched::Float64, !Matched::Float64)
   @ Main none:1

Stacktrace:
[...]

julia> f()
ERROR: MethodError: no method matching f()
The function `f` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  f(!Matched::Float64, !Matched::Float64)
   @ Main none:1
  f(!Matched::Number, !Matched::Number)
   @ Main none:1

Stacktrace:
[...]
```

Vous pouvez facilement voir quels méthodes existent pour une fonction en entrant l'objet fonction lui-même dans une session interactive :

```jldoctest fofxy
julia> f
f (generic function with 2 methods)
```

Cette sortie nous indique que `f` est un objet fonction avec deux méthodes. Pour découvrir quelles sont les signatures de ces méthodes, utilisez la fonction [`methods`](@ref) :

```jldoctest fofxy
julia> methods(f)
# 2 methods for generic function "f" from Main:
 [1] f(x::Float64, y::Float64)
     @ none:1
 [2] f(x::Number, y::Number)
     @ none:1
```

ce qui montre que `f` a deux méthodes, l'une prenant deux arguments `Float64` et l'autre prenant des arguments de type `Number`. Il indique également le fichier et le numéro de ligne où les méthodes ont été définies : comme ces méthodes ont été définies au REPL, nous obtenons le numéro de ligne apparent `none:1`.

En l'absence d'une déclaration de type avec `::`, le type d'un paramètre de méthode est `Any` par défaut, ce qui signifie qu'il n'est pas contraint puisque toutes les valeurs en Julia sont des instances du type abstrait `Any`. Ainsi, nous pouvons définir une méthode générale pour `f` comme suit :

```jldoctest fofxy
julia> f(x,y) = println("Whoa there, Nelly.")
f (generic function with 3 methods)

julia> methods(f)
# 3 methods for generic function "f" from Main:
 [1] f(x::Float64, y::Float64)
     @ none:1
 [2] f(x::Number, y::Number)
     @ none:1
 [3] f(x, y)
     @ none:1

julia> f("foo", 1)
Whoa there, Nelly.
```

Ce catch-all est moins spécifique que toute autre définition de méthode possible pour une paire de valeurs de paramètres, il ne sera donc appelé que sur des paires d'arguments auxquelles aucune autre définition de méthode ne s'applique.

Notez que dans la signature de la troisième méthode, aucun type n'est spécifié pour les arguments `x` et `y`. C'est une façon abrégée d'exprimer `f(x::Any, y::Any)`.

Bien que cela semble être un concept simple, le dispatch multiple sur les types de valeurs est peut-être la caractéristique la plus puissante et centrale du langage Julia. Les opérations de base ont généralement des dizaines de méthodes :

```julia-repl
julia> methods(+)
# 180 methods for generic function "+":
[1] +(x::Bool, z::Complex{Bool}) in Base at complex.jl:227
[2] +(x::Bool, y::Bool) in Base at bool.jl:89
[3] +(x::Bool) in Base at bool.jl:86
[4] +(x::Bool, y::T) where T<:AbstractFloat in Base at bool.jl:96
[5] +(x::Bool, z::Complex) in Base at complex.jl:234
[6] +(a::Float16, b::Float16) in Base at float.jl:373
[7] +(x::Float32, y::Float32) in Base at float.jl:375
[8] +(x::Float64, y::Float64) in Base at float.jl:376
[9] +(z::Complex{Bool}, x::Bool) in Base at complex.jl:228
[10] +(z::Complex{Bool}, x::Real) in Base at complex.jl:242
[11] +(x::Char, y::Integer) in Base at char.jl:40
[12] +(c::BigInt, x::BigFloat) in Base.MPFR at mpfr.jl:307
[13] +(a::BigInt, b::BigInt, c::BigInt, d::BigInt, e::BigInt) in Base.GMP at gmp.jl:392
[14] +(a::BigInt, b::BigInt, c::BigInt, d::BigInt) in Base.GMP at gmp.jl:391
[15] +(a::BigInt, b::BigInt, c::BigInt) in Base.GMP at gmp.jl:390
[16] +(x::BigInt, y::BigInt) in Base.GMP at gmp.jl:361
[17] +(x::BigInt, c::Union{UInt16, UInt32, UInt64, UInt8}) in Base.GMP at gmp.jl:398
...
[180] +(a, b, c, xs...) in Base at operators.jl:424
```

Le dispatch multiple, associé au système de types paramétriques flexible, donne à Julia sa capacité à exprimer de manière abstraite des algorithmes de haut niveau découplés des détails d'implémentation.

## [Method specializations](@id man-method-specializations)

Lorsque vous créez plusieurs méthodes de la même fonction, cela s'appelle parfois "spécialisation". Dans ce cas, vous spécialisez la *fonction* en ajoutant des méthodes supplémentaires : chaque nouvelle méthode est une nouvelle spécialisation de la fonction. Comme indiqué ci-dessus, ces spécialisations sont renvoyées par `methods`.

Il existe un autre type de spécialisation qui se produit sans intervention du programmeur : le compilateur de Julia peut automatiquement spécialiser la *méthode* pour les types d'arguments spécifiques utilisés. De telles spécialisations ne sont *pas* répertoriées par `methods`, car cela ne crée pas de nouvelles `Method`s, mais des outils comme [`@code_typed`](@ref) vous permettent d'inspecter de telles spécialisations.

Par exemple, si vous créez une méthode

```
mysum(x::Real, y::Real) = x + y
```

vous avez donné à la fonction `mysum` une nouvelle méthode (peut-être sa seule méthode), et cette méthode prend n'importe quelle paire d'entrées de nombres `Réels`. Mais si vous exécutez ensuite

```julia-repl
julia> mysum(1, 2)
3

julia> mysum(1.0, 2.0)
3.0
```

Julia compilera `mysum` deux fois, une fois pour `x::Int, y::Int` et à nouveau pour `x::Float64, y::Float64`. L'objectif de cette double compilation est la performance : les méthodes appelées pour `+` (que `mysum` utilise) varient en fonction des types spécifiques de `x` et `y`, et en compilant différentes spécialisations, Julia peut effectuer toutes les recherches de méthodes à l'avance. Cela permet au programme de s'exécuter beaucoup plus rapidement, car il n'a pas à se soucier de la recherche de méthodes pendant son exécution. La spécialisation automatique de Julia vous permet d'écrire des algorithmes génériques et de vous attendre à ce que le compilateur génère un code efficace et spécialisé pour gérer chaque cas dont vous avez besoin.

Dans les cas où le nombre de spécialisations potentielles pourrait être effectivement illimité, Julia peut éviter cette spécialisation par défaut. Voir [Be aware of when Julia avoids specializing](@ref) pour plus d'informations.

## [Method Ambiguities](@id man-ambiguities)

Il est possible de définir un ensemble de méthodes de fonction de sorte qu'il n'y ait pas de méthode la plus spécifique unique applicable à certaines combinaisons d'arguments :

```jldoctest gofxy
julia> g(x::Float64, y) = 2x + y
g (generic function with 1 method)

julia> g(x, y::Float64) = x + 2y
g (generic function with 2 methods)

julia> g(2.0, 3)
7.0

julia> g(2, 3.0)
8.0

julia> g(2.0, 3.0)
ERROR: MethodError: g(::Float64, ::Float64) is ambiguous.

Candidates:
  g(x, y::Float64)
    @ Main none:1
  g(x::Float64, y)
    @ Main none:1

Possible fix, define
  g(::Float64, ::Float64)

Stacktrace:
[...]
```

Ici, l'appel `g(2.0, 3.0)` pourrait être géré soit par la méthode `g(::Float64, ::Any)`, soit par la méthode `g(::Any, ::Float64)`. L'ordre dans lequel les méthodes sont définies n'a pas d'importance et aucune n'est plus spécifique que l'autre. Dans de tels cas, Julia lève une [`MethodError`](@ref) plutôt que de choisir arbitrairement une méthode. Vous pouvez éviter les ambiguïtés de méthode en spécifiant une méthode appropriée pour le cas d'intersection :

```jldoctest gofxy
julia> g(x::Float64, y::Float64) = 2x + 2y
g (generic function with 3 methods)

julia> g(2.0, 3)
7.0

julia> g(2, 3.0)
8.0

julia> g(2.0, 3.0)
10.0
```

Il est recommandé de définir d'abord la méthode de désambiguïsation, car sinon l'ambiguïté existe, même de manière transitoire, jusqu'à ce que la méthode plus spécifique soit définie.

Dans des cas plus complexes, la résolution des ambiguïtés de méthode implique un certain élément de conception ; ce sujet est exploré plus en détail [below](@ref man-method-design-ambiguities).

## Parametric Methods

Les définitions de méthode peuvent éventuellement avoir des paramètres de type qualifiant la signature :

```jldoctest same_typefunc
julia> same_type(x::T, y::T) where {T} = true
same_type (generic function with 1 method)

julia> same_type(x,y) = false
same_type (generic function with 2 methods)
```

La première méthode s'applique chaque fois que les deux arguments sont du même type concret, peu importe de quel type il s'agit, tandis que la deuxième méthode agit comme un attrape-tout, couvrant tous les autres cas. Ainsi, dans l'ensemble, cela définit une fonction booléenne qui vérifie si ses deux arguments sont du même type :

```jldoctest same_typefunc
julia> same_type(1, 2)
true

julia> same_type(1, 2.0)
false

julia> same_type(1.0, 2.0)
true

julia> same_type("foo", 2.0)
false

julia> same_type("foo", "bar")
true

julia> same_type(Int32(1), Int64(2))
false
```

De telles définitions correspondent à des méthodes dont les signatures de type sont des types `UnionAll` (voir [UnionAll Types](@ref)).

Ce type de définition du comportement des fonctions par dispatch est assez courant – même idiomatique – en Julia. Les paramètres de type de méthode ne sont pas limités à être utilisés comme types d'arguments : ils peuvent être utilisés partout où une valeur serait dans la signature de la fonction ou dans le corps de la fonction. Voici un exemple où le paramètre de type de méthode `T` est utilisé comme paramètre de type pour le type paramétrique `Vector{T}` dans la signature de la méthode :

```jldoctest
julia> function myappend(v::Vector{T}, x::T) where {T}
           return [v..., x]
       end
myappend (generic function with 1 method)
```

Le paramètre de type `T` dans cet exemple garantit que l'élément ajouté `x` est un sous-type du type existant de l'élément du vecteur `v`. Le mot-clé `where` introduit une liste de ces contraintes après la définition de la signature de la méthode. Cela fonctionne de la même manière pour les définitions en une ligne, comme vu ci-dessus, et doit apparaître *avant* le [return type declaration](@ref man-functions-return-type), si présent, comme illustré ci-dessous :

```jldoctest
julia> (myappend(v::Vector{T}, x::T)::Vector) where {T} = [v..., x]
myappend (generic function with 1 method)

julia> myappend([1,2,3],4)
4-element Vector{Int64}:
 1
 2
 3
 4

julia> myappend([1,2,3],2.5)
ERROR: MethodError: no method matching myappend(::Vector{Int64}, ::Float64)
The function `myappend` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  myappend(::Vector{T}, !Matched::T) where T
   @ Main none:1

Stacktrace:
[...]

julia> myappend([1.0,2.0,3.0],4.0)
4-element Vector{Float64}:
 1.0
 2.0
 3.0
 4.0

julia> myappend([1.0,2.0,3.0],4)
ERROR: MethodError: no method matching myappend(::Vector{Float64}, ::Int64)
The function `myappend` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  myappend(::Vector{T}, !Matched::T) where T
   @ Main none:1

Stacktrace:
[...]
```

Si le type de l'élément ajouté ne correspond pas au type d'élément du vecteur auquel il est ajouté, une [`MethodError`](@ref) est levée. Dans l'exemple suivant, le paramètre de type de la méthode `T` est utilisé comme valeur de retour :

```jldoctest
julia> mytypeof(x::T) where {T} = T
mytypeof (generic function with 1 method)

julia> mytypeof(1)
Int64

julia> mytypeof(1.0)
Float64
```

Tout comme vous pouvez imposer des contraintes de sous-type sur les paramètres de type dans les déclarations de type (voir [Parametric Types](@ref)), vous pouvez également contraindre les paramètres de type des méthodes :

```jldoctest
julia> same_type_numeric(x::T, y::T) where {T<:Number} = true
same_type_numeric (generic function with 1 method)

julia> same_type_numeric(x::Number, y::Number) = false
same_type_numeric (generic function with 2 methods)

julia> same_type_numeric(1, 2)
true

julia> same_type_numeric(1, 2.0)
false

julia> same_type_numeric(1.0, 2.0)
true

julia> same_type_numeric("foo", 2.0)
ERROR: MethodError: no method matching same_type_numeric(::String, ::Float64)
The function `same_type_numeric` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  same_type_numeric(!Matched::T, ::T) where T<:Number
   @ Main none:1
  same_type_numeric(!Matched::Number, ::Number)
   @ Main none:1

Stacktrace:
[...]

julia> same_type_numeric("foo", "bar")
ERROR: MethodError: no method matching same_type_numeric(::String, ::String)
The function `same_type_numeric` exists, but no method is defined for this combination of argument types.

julia> same_type_numeric(Int32(1), Int64(2))
false
```

La fonction `same_type_numeric` se comporte de manière similaire à la fonction `same_type` définie ci-dessus, mais n'est définie que pour les paires de nombres.

Les méthodes paramétriques permettent la même syntaxe que les expressions `where` utilisées pour écrire des types (voir [UnionAll Types](@ref)). S'il n'y a qu'un seul paramètre, les accolades englobantes (dans `where {T}`) peuvent être omises, mais sont souvent préférées pour plus de clarté. Plusieurs paramètres peuvent être séparés par des virgules, par exemple `where {T, S<:Real}`, ou écrits en utilisant des `where` imbriqués, par exemple `where S<:Real where T`.

## Redefining Methods

Lors de la redéfinition d'une méthode ou de l'ajout de nouvelles méthodes, il est important de réaliser que ces changements ne prennent pas effet immédiatement. C'est essentiel pour la capacité de Julia à inférer statiquement et à compiler du code pour s'exécuter rapidement, sans les astuces et les surcharges habituelles du JIT. En effet, toute nouvelle définition de méthode ne sera pas visible dans l'environnement d'exécution actuel, y compris les Tâches et les Threads (et toutes les fonctions `@generated` définies précédemment). Commençons par un exemple pour voir ce que cela signifie :

```julia-repl
julia> function tryeval()
           @eval newfun() = 1
           newfun()
       end
tryeval (generic function with 1 method)

julia> tryeval()
ERROR: MethodError: no method matching newfun()
The applicable method may be too new: running in world age xxxx1, while current world is xxxx2.
Closest candidates are:
  newfun() at none:1 (method too new to be called from this world context.)
 in tryeval() at none:1
 ...

julia> newfun()
1
```

Dans cet exemple, observez que la nouvelle définition pour `newfun` a été créée, mais ne peut pas être appelée immédiatement. Le nouveau global est immédiatement visible par la fonction `tryeval`, donc vous pourriez écrire `return newfun` (sans parenthèses). Mais ni vous, ni aucun de vos appelants, ni les fonctions qu'ils appellent, etc. ne peuvent appeler cette nouvelle définition de méthode !

Mais il y a une exception : les appels futurs à `newfun` *depuis le REPL* fonctionnent comme prévu, étant capables de voir et d'appeler la nouvelle définition de `newfun`.

Cependant, les appels futurs à `tryeval` continueront de voir la définition de `newfun` telle qu'elle était *à l'instruction précédente dans le REPL*, et donc avant cet appel à `tryeval`.

Vous voudrez peut-être essayer cela par vous-même pour voir comment cela fonctionne.

L'implémentation de ce comportement est un "compteur d'âge du monde". Cette valeur croissante de manière monotone suit chaque opération de définition de méthode. Cela permet de décrire "l'ensemble des définitions de méthodes visibles pour un environnement d'exécution donné" comme un seul nombre, ou "âge du monde". Cela permet également de comparer les méthodes disponibles dans deux mondes simplement en comparant leur valeur ordinale. Dans l'exemple ci-dessus, nous voyons que le "monde actuel" (dans lequel la méthode `newfun` existe) est un de plus que le "monde d'exécution" local à la tâche qui a été fixé lorsque l'exécution de `tryeval` a commencé.

Parfois, il est nécessaire de contourner cela (par exemple, si vous implémentez le REPL ci-dessus). Heureusement, il existe une solution facile : appelez la fonction en utilisant [`Base.invokelatest`](@ref) :

```jldoctest
julia> function tryeval2()
           @eval newfun2() = 2
           Base.invokelatest(newfun2)
       end
tryeval2 (generic function with 1 method)

julia> tryeval2()
2
```

Enfin, examinons quelques exemples plus complexes où cette règle entre en jeu. Définissez une fonction `f(x)`, qui a initialement une méthode :

```jldoctest redefinemethod
julia> f(x) = "original definition"
f (generic function with 1 method)
```

Commencez d'autres opérations qui utilisent `f(x)` :

```jldoctest redefinemethod
julia> g(x) = f(x)
g (generic function with 1 method)

julia> t = @async f(wait()); yield();
```

Maintenant, nous ajoutons de nouvelles méthodes à `f(x)` :

```jldoctest redefinemethod
julia> f(x::Int) = "definition for Int"
f (generic function with 2 methods)

julia> f(x::Type{Int}) = "definition for Type{Int}"
f (generic function with 3 methods)
```

Comparer comment ces résultats diffèrent :

```jldoctest redefinemethod
julia> f(1)
"definition for Int"

julia> g(1)
"definition for Int"

julia> fetch(schedule(t, 1))
"original definition"

julia> t = @async f(wait()); yield();

julia> fetch(schedule(t, 1))
"definition for Int"
```

## Design Patterns with Parametric Methods

Bien que la logique de dispatch complexe ne soit pas nécessaire pour la performance ou l'utilisabilité, il arrive parfois que ce soit le meilleur moyen d'exprimer un algorithme. Voici quelques modèles de conception courants qui apparaissent parfois lors de l'utilisation du dispatch de cette manière.

### Extracting the type parameter from a super-type

Voici un modèle de code correct pour retourner le type d'élément `T` de tout sous-type arbitraire de `AbstractArray` qui a un type d'élément bien défini :

```julia
abstract type AbstractArray{T, N} end
eltype(::Type{<:AbstractArray{T}}) where {T} = T
```

en utilisant ce qu'on appelle le dispatch triangulaire. Notez que les types `UnionAll`, par exemple `eltype(AbstractArray{T} where T <: Integer)`, ne correspondent pas à la méthode ci-dessus. L'implémentation de `eltype` dans `Base` ajoute une méthode de secours à `Any` pour de tels cas.

Une erreur courante consiste à essayer d'obtenir le type d'élément en utilisant l'introspection :

```julia
eltype_wrong(::Type{A}) where {A<:AbstractArray} = A.parameters[1]
```

Cependant, il n'est pas difficile de construire des cas où cela échouera :

```julia
struct BitVector <: AbstractArray{Bool, 1}; end
```

Ici, nous avons créé un type `BitVector` qui n'a pas de paramètres, mais où le type d'élément est toujours entièrement spécifié, avec `T` égal à `Bool` !

Une autre erreur consiste à essayer de parcourir la hiérarchie des types en utilisant `supertype` :

```julia
eltype_wrong(::Type{AbstractArray{T}}) where {T} = T
eltype_wrong(::Type{AbstractArray{T, N}}) where {T, N} = T
eltype_wrong(::Type{A}) where {A<:AbstractArray} = eltype_wrong(supertype(A))
```

Bien que cela fonctionne pour les types déclarés, cela échoue pour les types sans supertypes :

```julia-repl
julia> eltype_wrong(Union{AbstractArray{Int}, AbstractArray{Float64}})
ERROR: MethodError: no method matching supertype(::Type{Union{AbstractArray{Float64,N} where N, AbstractArray{Int64,N} where N}})
Closest candidates are:
  supertype(::DataType) at operators.jl:43
  supertype(::UnionAll) at operators.jl:48
```

### Building a similar type with a different type parameter

Lors de la construction de code générique, il est souvent nécessaire de créer un objet similaire avec quelques modifications apportées à la structure du type, ce qui nécessite également un changement des paramètres de type. Par exemple, vous pourriez avoir une sorte de tableau abstrait avec un type d'élément arbitraire et vouloir écrire votre calcul dessus avec un type d'élément spécifique. Nous devons implémenter une méthode pour chaque sous-type `AbstractArray{T}` qui décrit comment effectuer cette transformation de type. Il n'existe pas de transformation générale d'un sous-type en un autre sous-type avec un paramètre différent.

Les sous-types de `AbstractArray` implémentent généralement deux méthodes pour y parvenir : une méthode pour convertir le tableau d'entrée en un sous-type d'un type abstrait spécifique `AbstractArray{T, N}` ; et une méthode pour créer un nouveau tableau non initialisé avec un type d'élément spécifique. Des exemples d'implémentation de ceux-ci peuvent être trouvés dans Julia Base. Voici un exemple d'utilisation de base de ceux-ci, garantissant que `input` et `output` sont du même type :

```julia
input = convert(AbstractArray{Eltype}, input)
output = similar(input, Eltype)
```

En tant qu'extension de cela, dans les cas où l'algorithme a besoin d'une copie du tableau d'entrée, [`convert`](@ref) est insuffisant car la valeur de retour peut faire référence à l'entrée originale. Combiner [`similar`](@ref) (pour créer le tableau de sortie) et [`copyto!`](@ref) (pour le remplir avec les données d'entrée) est une manière générique d'exprimer le besoin d'une copie mutable de l'argument d'entrée :

```julia
copy_with_eltype(input, Eltype) = copyto!(similar(input, Eltype), input)
```

### Iterated dispatch

Pour dispatcher une liste d'arguments paramétriques à plusieurs niveaux, il est souvent préférable de séparer chaque niveau de dispatch en fonctions distinctes. Cela peut sembler similaire dans l'approche au dispatch simple, mais comme nous le verrons ci-dessous, c'est néanmoins plus flexible.

Par exemple, essayer de dispatcher sur le type d'élément d'un tableau rencontrera souvent des situations ambiguës. Au lieu de cela, le code dispatchera généralement d'abord sur le type de conteneur, puis se récursivera vers une méthode plus spécifique basée sur eltype. Dans la plupart des cas, les algorithmes se prêtent commodément à cette approche hiérarchique, tandis que dans d'autres cas, cette rigueur doit être résolue manuellement. Ce branchement de dispatching peut être observé, par exemple, dans la logique pour sommer deux matrices :

```julia
# First dispatch selects the map algorithm for element-wise summation.
+(a::Matrix, b::Matrix) = map(+, a, b)
# Then dispatch handles each element and selects the appropriate
# common element type for the computation.
+(a, b) = +(promote(a, b)...)
# Once the elements have the same type, they can be added.
# For example, via primitive operations exposed by the processor.
+(a::Float64, b::Float64) = Core.add(a, b)
```

### Trait-based dispatch

Une extension naturelle à l'envoi itéré ci-dessus est d'ajouter une couche à la sélection de méthode qui permet de dispatcher sur des ensembles de types qui sont indépendants des ensembles définis par la hiérarchie des types. Nous pourrions construire un tel ensemble en écrivant une `Union` des types en question, mais cet ensemble ne serait pas extensible car les types `Union` ne peuvent pas être modifiés après leur création. Cependant, un tel ensemble extensible peut être programmé avec un modèle de conception souvent appelé ["Holy-trait"](https://github.com/JuliaLang/julia/issues/2345#issuecomment-54537633).

Ce modèle est mis en œuvre en définissant une fonction générique qui calcule une valeur (ou un type) singleton différente pour chaque ensemble de traits auquel les arguments de la fonction peuvent appartenir. Si cette fonction est pure, il n'y a aucun impact sur les performances par rapport à un dispatch normal.

L'exemple de la section précédente a omis les détails d'implémentation de [`map`](@ref) et [`promote`](@ref), qui fonctionnent tous deux en termes de ces traits. Lors de l'itération sur une matrice, comme dans l'implémentation de `map`, une question importante est quel ordre utiliser pour parcourir les données. Lorsque les sous-types de `AbstractArray` implémentent le trait [`Base.IndexStyle`](@ref), d'autres fonctions telles que `map` peuvent s'appuyer sur ces informations pour choisir le meilleur algorithme (voir [Abstract Array Interface](@ref man-interface-array)). Cela signifie que chaque sous-type n'a pas besoin d'implémenter une version personnalisée de `map`, puisque les définitions génériques + classes de traits permettront au système de sélectionner la version la plus rapide. Voici une implémentation simplifiée de `map` illustrant le dispatch basé sur les traits :

```julia
map(f, a::AbstractArray, b::AbstractArray) = map(Base.IndexStyle(a, b), f, a, b)
# generic implementation:
map(::Base.IndexCartesian, f, a::AbstractArray, b::AbstractArray) = ...
# linear-indexing implementation (faster)
map(::Base.IndexLinear, f, a::AbstractArray, b::AbstractArray) = ...
```

Cette approche basée sur les traits est également présente dans le mécanisme [`promote`](@ref) utilisé par le scalaire `+`. Il utilise [`promote_type`](@ref), qui renvoie le type commun optimal pour effectuer l'opération donnée les deux types des opérandes. Cela permet de réduire le problème de l'implémentation de chaque fonction pour chaque paire de types d'arguments possibles, au problème beaucoup plus petit de l'implémentation d'une opération de conversion de chaque type vers un type commun, plus une table de règles de promotion préférées par paires.

### Output-type computation

La discussion sur la promotion basée sur les traits fournit une transition vers notre prochain modèle de conception : le calcul du type d'élément de sortie pour une opération matricielle.

Pour implémenter des opérations primitives, telles que l'addition, nous utilisons la fonction [`promote_type`](@ref) pour calculer le type de sortie souhaité. (Comme auparavant, nous avons vu cela à l'œuvre dans l'appel à `promote` dans l'appel à `+`).

Pour des fonctions plus complexes sur les matrices, il peut être nécessaire de calculer le type de retour attendu pour une séquence d'opérations plus complexe. Cela se fait souvent par les étapes suivantes :

1. Write a small function `op` that expresses the set of operations performed by the kernel of the algorithm.
2. Calculez le type d'élément `R` de la matrice résultante comme `promote_op(op, argument_types...)`, où `argument_types` est calculé à partir de `eltype` appliqué à chaque tableau d'entrée.
3. Construisez la matrice de sortie en tant que `similar(R, dims)`, où `dims` sont les dimensions souhaitées du tableau de sortie.

Pour un exemple plus spécifique, un pseudo-code générique de multiplication de matrices carrées pourrait ressembler à :

```julia
function matmul(a::AbstractMatrix, b::AbstractMatrix)
    op = (ai, bi) -> ai * bi + ai * bi

    ## this is insufficient because it assumes `one(eltype(a))` is constructable:
    # R = typeof(op(one(eltype(a)), one(eltype(b))))

    ## this fails because it assumes `a[1]` exists and is representative of all elements of the array
    # R = typeof(op(a[1], b[1]))

    ## this is incorrect because it assumes that `+` calls `promote_type`
    ## but this is not true for some types, such as Bool:
    # R = promote_type(ai, bi)

    # this is wrong, since depending on the return value
    # of type-inference is very brittle (as well as not being optimizable):
    # R = Base.return_types(op, (eltype(a), eltype(b)))

    ## but, finally, this works:
    R = promote_op(op, eltype(a), eltype(b))
    ## although sometimes it may give a larger type than desired
    ## it will always give a correct type

    output = similar(b, R, (size(a, 1), size(b, 2)))
    if size(a, 2) > 0
        for j in 1:size(b, 2)
            for i in 1:size(a, 1)
                ## here we don't use `ab = zero(R)`,
                ## since `R` might be `Any` and `zero(Any)` is not defined
                ## we also must declare `ab::R` to make the type of `ab` constant in the loop,
                ## since it is possible that typeof(a * b) != typeof(a * b + a * b) == R
                ab::R = a[i, 1] * b[1, j]
                for k in 2:size(a, 2)
                    ab += a[i, k] * b[k, j]
                end
                output[i, j] = ab
            end
        end
    end
    return output
end
```

### Separate convert and kernel logic

Une façon de réduire considérablement les temps de compilation et la complexité des tests est d'isoler la logique de conversion au type souhaité et le calcul. Cela permet au compilateur de spécialiser et d'inliner la logique de conversion indépendamment du reste du corps du noyau plus large.

C'est un modèle courant observé lors de la conversion d'une classe de types plus large vers le type d'argument spécifique qui est réellement pris en charge par l'algorithme :

```julia
complexfunction(arg::Int) = ...
complexfunction(arg::Any) = complexfunction(convert(Int, arg))

matmul(a::T, b::T) = ...
matmul(a, b) = matmul(promote(a, b)...)
```

## Parametrically-constrained Varargs methods

Les paramètres de fonction peuvent également être utilisés pour contraindre le nombre d'arguments qui peuvent être fournis à une fonction "varargs" ([Varargs Functions](@ref)). La notation `Vararg{T,N}` est utilisée pour indiquer une telle contrainte. Par exemple :

```jldoctest
julia> bar(a,b,x::Vararg{Any,2}) = (a,b,x)
bar (generic function with 1 method)

julia> bar(1,2,3)
ERROR: MethodError: no method matching bar(::Int64, ::Int64, ::Int64)
The function `bar` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  bar(::Any, ::Any, ::Any, !Matched::Any)
   @ Main none:1

Stacktrace:
[...]

julia> bar(1,2,3,4)
(1, 2, (3, 4))

julia> bar(1,2,3,4,5)
ERROR: MethodError: no method matching bar(::Int64, ::Int64, ::Int64, ::Int64, ::Int64)
The function `bar` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  bar(::Any, ::Any, ::Any, ::Any)
   @ Main none:1

Stacktrace:
[...]
```

Plus utilement, il est possible de contraindre les méthodes varargs par un paramètre. Par exemple :

```julia
function getindex(A::AbstractArray{T,N}, indices::Vararg{Number,N}) where {T,N}
```

serait appelé uniquement lorsque le nombre d'`indices` correspond à la dimensionnalité du tableau.

Lorsque seul le type des arguments fournis doit être contraint, `Vararg{T}` peut être écrit de manière équivalente comme `T...`. Par exemple, `f(x::Int...) = x` est un raccourci pour `f(x::Vararg{Int}) = x`.

## Note on Optional and keyword Arguments

Comme mentionné brièvement dans [Functions](@ref man-functions), les arguments optionnels sont implémentés comme une syntaxe pour plusieurs définitions de méthodes. Par exemple, cette définition :

```julia
f(a=1,b=2) = a+2b
```

se traduit par les trois méthodes suivantes :

```julia
f(a,b) = a+2b
f(a) = f(a,2)
f() = f(1,2)
```

Cela signifie que l'appel de `f()` est équivalent à l'appel de `f(1,2)`. Dans ce cas, le résultat est `5`, car `f(1,2)` invoque la première méthode de `f` ci-dessus. Cependant, cela ne doit pas toujours être le cas. Si vous définissez une quatrième méthode qui est plus spécialisée pour les entiers :

```julia
f(a::Int,b::Int) = a-2b
```

alors le résultat de `f()` et de `f(1,2)` est `-3`. En d'autres termes, les arguments optionnels sont liés à une fonction, et non à une méthode spécifique de cette fonction. Cela dépend des types des arguments optionnels quelle méthode est invoquée. Lorsque les arguments optionnels sont définis en termes d'une variable globale, le type de l'argument optionnel peut même changer à l'exécution.

Les arguments de mot-clé se comportent de manière assez différente des arguments positionnels ordinaires. En particulier, ils ne participent pas à la dispatch des méthodes. Les méthodes sont dispatchées uniquement en fonction des arguments positionnels, les arguments de mot-clé étant traités après que la méthode correspondante a été identifiée.

## Function-like objects

Les méthodes sont associées à des types, il est donc possible de rendre n'importe quel objet Julia "appelable" en ajoutant des méthodes à son type. (De tels objets "appelables" sont parfois appelés "foncteurs".)

Par exemple, vous pouvez définir un type qui stocke les coefficients d'un polynôme, mais qui se comporte comme une fonction évaluant le polynôme :

```jldoctest polynomial
julia> struct Polynomial{R}
           coeffs::Vector{R}
       end

julia> function (p::Polynomial)(x)
           v = p.coeffs[end]
           for i = (length(p.coeffs)-1):-1:1
               v = v*x + p.coeffs[i]
           end
           return v
       end

julia> (p::Polynomial)() = p(5)
```

Remarquez que la fonction est spécifiée par type plutôt que par nom. Comme avec les fonctions normales, il existe une forme de syntaxe concise. Dans le corps de la fonction, `p` fera référence à l'objet qui a été appelé. Un `Polynomial` peut être utilisé comme suit :

```jldoctest polynomial
julia> p = Polynomial([1,10,100])
Polynomial{Int64}([1, 10, 100])

julia> p(3)
931

julia> p()
2551
```

Ce mécanisme est également la clé de la façon dont les constructeurs de type et les fermetures (fonctions internes qui se réfèrent à leur environnement environnant) fonctionnent en Julia.

## Empty generic functions

Il est parfois utile d'introduire une fonction générique sans encore ajouter de méthodes. Cela peut être utilisé pour séparer les définitions d'interface des implémentations. Cela peut également être fait dans le but de documentation ou de lisibilité du code. La syntaxe pour cela est un bloc `function` vide sans un tuple d'arguments :

```julia
function emptyfunc end
```

## [Method design and the avoidance of ambiguities](@id man-method-design-ambiguities)

Le polymorphisme des méthodes de Julia est l'une de ses caractéristiques les plus puissantes, mais exploiter ce pouvoir peut poser des défis de conception. En particulier, dans des hiérarchies de méthodes plus complexes, il n'est pas rare que [ambiguities](@ref man-ambiguities) se produise.

Au-dessus, il a été souligné qu'on peut résoudre des ambiguïtés comme

```julia
f(x, y::Int) = 1
f(x::Int, y) = 2
```

en définissant une méthode

```julia
f(x::Int, y::Int) = 3
```

C'est souvent la bonne stratégie ; cependant, il existe des circonstances où suivre ce conseil de manière aveugle peut être contre-productif. En particulier, plus une fonction générique a de méthodes, plus il y a de possibilités d'ambiguïtés. Lorsque vos hiérarchies de méthodes deviennent plus compliquées que cet exemple simple, il peut être judicieux de réfléchir attentivement à des stratégies alternatives.

Ci-dessous, nous discutons des défis particuliers et de certaines alternatives pour résoudre de tels problèmes.

### Tuple and NTuple arguments

`Tuple` (et `NTuple`) les arguments présentent des défis particuliers. Par exemple,

```julia
f(x::NTuple{N,Int}) where {N} = 1
f(x::NTuple{N,Float64}) where {N} = 2
```

sont ambiguës en raison de la possibilité que `N == 0` : il n'y a pas d'éléments pour déterminer si la variante `Int` ou `Float64` doit être appelée. Pour résoudre l'ambiguïté, une approche consiste à définir une méthode pour le tuple vide :

```julia
f(x::Tuple{}) = 3
```

Alternativement, pour toutes les méthodes sauf une, vous pouvez insister sur le fait qu'il y a au moins un élément dans le tuple :

```julia
f(x::NTuple{N,Int}) where {N} = 1           # this is the fallback
f(x::Tuple{Float64, Vararg{Float64}}) = 2   # this requires at least one Float64
```

### [Orthogonalize your design](@id man-methods-orthogonalize)

Lorsque vous pourriez être tenté de dispatcher sur deux arguments ou plus, envisagez si une fonction "wrapper" pourrait simplifier la conception. Par exemple, au lieu d'écrire plusieurs variantes :

```julia
f(x::A, y::A) = ...
f(x::A, y::B) = ...
f(x::B, y::A) = ...
f(x::B, y::B) = ...
```

vous pourriez envisager de définir

```julia
f(x::A, y::A) = ...
f(x, y) = f(g(x), g(y))
```

où `g` convertit l'argument en type `A`. C'est un exemple très spécifique du principe plus général de [orthogonal design](https://en.wikipedia.org/wiki/Orthogonality_(programming)), dans lequel des concepts séparés sont attribués à des méthodes séparées. Ici, `g` aura très probablement besoin d'une définition de secours.

```julia
g(x::A) = x
```

Une stratégie connexe exploite `promote` pour amener `x` et `y` à un type commun :

```julia
f(x::T, y::T) where {T} = ...
f(x, y) = f(promote(x, y)...)
```

Un risque avec ce design est la possibilité que, s'il n'existe pas de méthode de promotion appropriée convertissant `x` et `y` au même type, la deuxième méthode se rappelle indéfiniment et déclenche un débordement de pile.

### Dispatch on one argument at a time

Si vous devez dispatcher sur plusieurs arguments, et qu'il y a de nombreux fallback avec trop de combinaisons pour rendre pratique la définition de toutes les variantes possibles, envisagez d'introduire une "cascade de noms" où (par exemple) vous dispatchiez sur le premier argument et appeliez ensuite une méthode interne :

```julia
f(x::A, y) = _fA(x, y)
f(x::B, y) = _fB(x, y)
```

Alors, les méthodes internes `_fA` et `_fB` peuvent dispatcher sur `y` sans se soucier des ambiguïtés entre elles par rapport à `x`.

Soyez conscient que cette stratégie présente au moins un inconvénient majeur : dans de nombreux cas, il n'est pas possible pour les utilisateurs de personnaliser davantage le comportement de `f` en définissant d'autres spécialisations de votre fonction exportée `f`. Au lieu de cela, ils doivent définir des spécialisations pour vos méthodes internes `_fA` et `_fB`, ce qui brouille les frontières entre les méthodes exportées et internes.

### Abstract containers and element types

Dans la mesure du possible, essayez d'éviter de définir des méthodes qui se basent sur des types d'éléments spécifiques de conteneurs abstraits. Par exemple,

```julia
-(A::AbstractArray{T}, b::Date) where {T<:Date}
```

génère des ambiguïtés pour quiconque définit une méthode

```julia
-(A::MyArrayType{T}, b::T) where {T}
```

La meilleure approche est d'éviter de définir *l'un* de ces méthodes : au lieu de cela, reposez-vous sur une méthode générique `-(A::AbstractArray, b)` et assurez-vous que cette méthode est implémentée avec des appels génériques (comme `similar` et `-`) qui font ce qu'il faut pour chaque type de conteneur et type d'élément *séparément*. C'est juste une variante plus complexe du conseil de [orthogonalize](@ref man-methods-orthogonalize) vos méthodes.

Lorsque cette approche n'est pas possible, il peut être utile de commencer une discussion avec d'autres développeurs sur la résolution de l'ambiguïté ; le fait qu'une méthode ait été définie en premier ne signifie pas nécessairement qu'elle ne peut pas être modifiée ou éliminée. En dernier recours, un développeur peut définir la méthode "pansement".

```julia
-(A::MyArrayType{T}, b::Date) where {T<:Date} = ...
```

cela résout l'ambiguïté par la force brute.

### Complex method "cascades" with default arguments

Si vous définissez une méthode "cascade" qui fournit des valeurs par défaut, faites attention à ne pas omettre d'arguments qui correspondent à des valeurs par défaut potentielles. Par exemple, supposons que vous écriviez un algorithme de filtrage numérique et que vous ayez une méthode qui gère les bords du signal en appliquant un remplissage :

```julia
function myfilter(A, kernel, ::Replicate)
    Apadded = replicate_edges(A, size(kernel))
    myfilter(Apadded, kernel)  # now perform the "real" computation
end
```

Cela va à l'encontre d'une méthode qui fournit un remplissage par défaut :

```julia
myfilter(A, kernel) = myfilter(A, kernel, Replicate()) # replicate the edge by default
```

Ensemble, ces deux méthodes génèrent une récursion infinie avec `A` qui devient constamment plus grand.

Le meilleur design serait de définir votre hiérarchie d'appels comme ceci :

```julia
struct NoPad end  # indicate that no padding is desired, or that it's already applied

myfilter(A, kernel) = myfilter(A, kernel, Replicate())  # default boundary conditions

function myfilter(A, kernel, ::Replicate)
    Apadded = replicate_edges(A, size(kernel))
    myfilter(Apadded, kernel, NoPad())  # indicate the new boundary conditions
end

# other padding methods go here

function myfilter(A, kernel, ::NoPad)
    # Here's the "real" implementation of the core computation
end
```

`NoPad` est fourni dans la même position d'argument que tout autre type de remplissage, ce qui maintient la hiérarchie de dispatch bien organisée et réduit la probabilité d'ambiguïtés. De plus, il étend l'interface "publique" `myfilter` : un utilisateur qui souhaite contrôler le remplissage de manière explicite peut appeler directement la variante `NoPad`.

## Defining methods in local scope

Vous pouvez définir des méthodes dans un [local scope](@ref scope-of-variables), par exemple

```jldoctest
julia> function f(x)
           g(y::Int) = y + x
           g(y) = y - x
           g
       end
f (generic function with 1 method)

julia> h = f(3);

julia> h(4)
7

julia> h(4.0)
1.0
```

Cependant, vous ne devez *pas* définir des méthodes locales de manière conditionnelle ou soumise à un flux de contrôle, comme dans

```julia
function f2(inc)
    if inc
        g(x) = x + 1
    else
        g(x) = x - 1
    end
end

function f3()
    function g end
    return g
    g() = 0
end
```

comme il n'est pas clair quelle fonction finira par être définie. À l'avenir, il pourrait être une erreur de définir des méthodes locales de cette manière.

Pour des cas comme celui-ci, utilisez plutôt des fonctions anonymes :

```julia
function f2(inc)
    g = if inc
        x -> x + 1
    else
        x -> x - 1
    end
end
```

[^Clarke61]: Arthur C. Clarke, *Profiles of the Future* (1961): Clarke's Third Law.
