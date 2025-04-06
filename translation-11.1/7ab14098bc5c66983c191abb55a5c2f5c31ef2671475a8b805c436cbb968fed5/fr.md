# Style Guide

Les sections suivantes expliquent quelques aspects du style de codage idiomatique en Julia. Aucune de ces règles n'est absolue ; ce ne sont que des suggestions pour vous aider à vous familiariser avec le langage et à vous aider à choisir parmi des conceptions alternatives.

## Indentation

Utilisez 4 espaces par niveau d'indentation.

## Write functions, not just scripts

Écrire du code sous forme de séries d'étapes au niveau supérieur est un moyen rapide de commencer à résoudre un problème, mais vous devriez essayer de diviser un programme en fonctions dès que possible. Les fonctions sont plus réutilisables et testables, et clarifient quelles étapes sont effectuées et quels sont leurs entrées et sorties. De plus, le code à l'intérieur des fonctions a tendance à s'exécuter beaucoup plus rapidement que le code au niveau supérieur, en raison du fonctionnement du compilateur de Julia.

Il convient également de souligner que les fonctions doivent prendre des arguments, au lieu d'opérer directement sur des variables globales (à l'exception des constantes comme [`pi`](@ref)).

## Avoid writing overly-specific types

Le code doit être aussi générique que possible. Au lieu d'écrire :

```julia
Complex{Float64}(x)
```

il est préférable d'utiliser les fonctions génériques disponibles :

```julia
complex(float(x))
```

La deuxième version convertira `x` en un type approprié, au lieu d'utiliser toujours le même type.

Ce point de style est particulièrement pertinent pour les arguments de fonction. Par exemple, ne déclarez pas un argument comme étant de type `Int` ou [`Int32`](@ref) s'il peut vraiment être n'importe quel entier, exprimé avec le type abstrait [`Integer`](@ref). En fait, dans de nombreux cas, vous pouvez omettre complètement le type d'argument, à moins qu'il ne soit nécessaire pour disambiguïser d'autres définitions de méthode, puisque [`MethodError`](@ref) sera de toute façon levé si un type est passé qui ne prend pas en charge l'une des opérations requises. (Ceci est connu sous le nom de [duck typing](https://en.wikipedia.org/wiki/Duck_typing).)

Par exemple, considérez les définitions suivantes d'une fonction `addone` qui retourne un plus son argument :

```julia
addone(x::Int) = x + 1                 # works only for Int
addone(x::Integer) = x + oneunit(x)    # any integer type
addone(x::Number) = x + oneunit(x)     # any numeric type
addone(x) = x + oneunit(x)             # any type supporting + and oneunit
```

La dernière définition de `addone` gère tout type prenant en charge [`oneunit`](@ref) (qui retourne 1 dans le même type que `x`, ce qui évite une promotion de type indésirable) et la fonction [`+`](@ref) avec ces arguments. La chose clé à réaliser est qu'il n'y a *aucun coût de performance* à définir *uniquement* le général `addone(x) = x + oneunit(x)`, car Julia compilera automatiquement des versions spécialisées au besoin. Par exemple, la première fois que vous appelez `addone(12)`, Julia compilera automatiquement une fonction `addone` spécialisée pour les arguments `x::Int`, avec l'appel à `oneunit` remplacé par sa valeur en ligne `1`. Par conséquent, les trois premières définitions de `addone` ci-dessus sont complètement redondantes avec la quatrième définition.

## Handle excess argument diversity in the caller

Au lieu de :

```julia
function foo(x, y)
    x = Int(x); y = Int(y)
    ...
end
foo(x, y)
```

utiliser :

```julia
function foo(x::Int, y::Int)
    ...
end
foo(Int(x), Int(y))
```

C'est un meilleur style car `foo` n'accepte pas vraiment des nombres de tous types ; il a vraiment besoin de `Int`.

Un problème ici est que si une fonction nécessite intrinsèquement des entiers, il pourrait être préférable de forcer l'appelant à décider comment les non-entiers doivent être convertis (par exemple, arrondi à l'entier inférieur ou supérieur). Un autre problème est que déclarer des types plus spécifiques laisse plus d'"espace" pour de futures définitions de méthodes.

## [Append `!` to names of functions that modify their arguments](@id bang-convention)

Au lieu de :

```julia
function double(a::AbstractArray{<:Number})
    for i in eachindex(a)
        a[i] *= 2
    end
    return a
end
```

utiliser :

```julia
function double!(a::AbstractArray{<:Number})
    for i in eachindex(a)
        a[i] *= 2
    end
    return a
end
```

Julia Base utilise cette convention tout au long et contient des exemples de fonctions avec des formes de copie et de modification (par exemple, [`sort`](@ref) et [`sort!`](@ref)), et d'autres qui ne font que modifier (par exemple, [`push!`](@ref), [`pop!`](@ref), [`splice!`](@ref)). Il est typique que de telles fonctions retournent également le tableau modifié pour plus de commodité.

Les fonctions liées à l'IO ou utilisant des générateurs de nombres aléatoires (RNG) sont des exceptions notables : Étant donné que ces fonctions doivent presque invariablement muter l'IO ou le RNG, les fonctions se terminant par `!` sont utilisées pour signifier une mutation *autre* que la mutation de l'IO ou l'avancement de l'état du RNG. Par exemple, `rand(x)` mute le RNG, tandis que `rand!(x)` mute à la fois le RNG et `x` ; de même, `read(io)` mute `io`, tandis que `read!(io, x)` mute les deux arguments.

## Avoid strange type `Union`s

Des types tels que `Union{Function,AbstractString}` sont souvent un signe qu'un certain design pourrait être plus clair.

## Avoid elaborate container types

Il n'est généralement pas très utile de construire des tableaux comme les suivants :

```julia
a = Vector{Union{Int,AbstractString,Tuple,Array}}(undef, n)
```

Dans ce cas, `Vector{Any}(undef, n)` est préférable. Il est également plus utile pour le compilateur d'annoter des utilisations spécifiques (par exemple, `a[i]::Int`) que d'essayer de regrouper de nombreuses alternatives dans un seul type.

## Prefer exported methods over direct field access

Le code idiomatique en Julia devrait généralement traiter les méthodes exportées d'un module comme l'interface de ses types. Les champs d'un objet sont généralement considérés comme des détails d'implémentation et le code utilisateur ne devrait y accéder directement que si cela est indiqué comme faisant partie de l'API. Cela présente plusieurs avantages :

  * Les développeurs de packages ont plus de liberté pour modifier l'implémentation sans casser le code des utilisateurs.
  * Les méthodes peuvent être passées à des constructions d'ordre supérieur comme [`map`](@ref) (par exemple `map(imag, zs)`) plutôt que `[z.im for z in zs]`).
  * Les méthodes peuvent être définies sur des types abstraits.
  * Les méthodes peuvent décrire une opération conceptuelle qui peut être partagée entre des types disparates (par exemple, `real(z)` fonctionne sur des nombres complexes ou des quaternions).

Le système de dispatch de Julia encourage ce style car `play(x::MyType)` ne définit la méthode `play` que pour ce type particulier, laissant aux autres types le soin d'avoir leur propre implémentation.

De même, les fonctions non exportées sont généralement internes et sujettes à des modifications, sauf indication contraire dans la documentation. Les noms reçoivent parfois un préfixe (ou suffixe) `_` pour suggérer davantage que quelque chose est "interne" ou un détail d'implémentation, mais ce n'est pas une règle.

Les contre-exemples à cette règle incluent [`NamedTuple`](@ref), [`RegexMatch`](@ref match), [`StatStruct`](@ref stat).

## Use naming conventions consistent with Julia `base/`

  * les modules et les noms de type utilisent la capitalisation et le camel case : `module SparseArrays`, `struct UnitRange`.
  * les*fonctions*sont*en*minuscules([`maximum`](@ref), [`convert`](@ref)) et, lorsqu'elles*sont*lisibles, avec*plusieurs*mots*collés*ensemble([`isequal`](@ref), [`haskey`](@ref)). Lorsque*c'est*nécessaire, utilisez*des*underscores*comme*séparateurs*de*mots. Les*underscores*sont*également*utilisés*pour*indiquer*une*combinaison*de*concepts([`remotecall_fetch`](@ref) comme*une*implémentation*plus*efficace*de `fetch(remotecall(...))`) ou*comme_modificateurs.
  * les fonctions modifiant au moins un de leurs arguments se terminent par `!`.
  * la concision est valorisée, mais évitez les abréviations ([`indexin`](@ref) plutôt que `indxin`) car il devient difficile de se souvenir si et comment certains mots sont abrégés.

Si un nom de fonction nécessite plusieurs mots, envisagez s'il pourrait représenter plus d'un concept et pourrait être mieux divisé en morceaux.

## Write functions with argument ordering similar to Julia Base

En règle générale, la bibliothèque de base utilise l'ordre suivant des arguments pour les fonctions, le cas échéant :

1. **Argument de fonction**. Mettre un argument de fonction en premier permet d'utiliser des blocs [`do`](@ref) pour passer des fonctions anonymes multilignes.
2. **Flux I/O**. Spécifier d'abord l'objet `IO` permet de passer la fonction à des fonctions telles que [`sprint`](@ref), par exemple `sprint(show, x)`.
3. **Entrée en mutation**. Par exemple, dans [`fill!(x, v)`](@ref fill!), `x` est l'objet en mutation et il apparaît avant la valeur à insérer dans `x`.
4. **Type**. Passer un type signifie généralement que la sortie aura le type donné. Dans [`parse(Int, "1")`](@ref parse), le type apparaît avant la chaîne à analyser. Il existe de nombreux exemples où le type apparaît en premier, mais il est utile de noter que dans [`read(io, String)`](@ref read), l'argument `IO` apparaît avant le type, ce qui est conforme à l'ordre décrit ici.
5. **L'entrée n'est pas mutée**. Dans `fill!(x, v)`, `v` n'est *pas* muté et il vient après `x`.
6. **Clé**. Pour les collections associatives, il s'agit de la clé de la ou des paires clé-valeur. Pour d'autres collections indexées, il s'agit de l'index.
7. **Valeur**. Pour les collections associatives, c'est la valeur de la ou des paires clé-valeur. Dans des cas comme [`fill!(x, v)`](@ref fill!), c'est `v`.
8. **Tout le reste**. Tous les autres arguments.
9. **Varargs**. Cela fait référence à des arguments qui peuvent être listés indéfiniment à la fin d'un appel de fonction. Par exemple, dans `Matrix{T}(undef, dims)`, les dimensions peuvent être données sous la forme d'un [`Tuple`](@ref), par exemple `Matrix{T}(undef, (1,2))`, ou sous la forme de [`Vararg`](@ref), par exemple `Matrix{T}(undef, 1, 2)`.
10. **Arguments de mot-clé**. Dans Julia, les arguments de mot-clé doivent de toute façon venir en dernier dans les définitions de fonction ; ils sont listés ici pour des raisons de complétude.

La grande majorité des fonctions ne prendra pas tous les types d'arguments énumérés ci-dessus ; les numéros ne font que désigner la priorité qui doit être utilisée pour les arguments applicables à une fonction.

Il y a bien sûr quelques exceptions. Par exemple, dans [`convert`](@ref), le type doit toujours venir en premier. Dans [`setindex!`](@ref), la valeur vient avant les indices afin que les indices puissent être fournis en tant que varargs.

Lors de la conception d'APIs, respecter cet ordre général autant que possible est susceptible d'offrir aux utilisateurs de vos fonctions une expérience plus cohérente.

## Don't overuse try-catch

Il vaut mieux éviter les erreurs que de compter sur leur détection.

## Don't parenthesize conditions

Julia n'exige pas de parenthèses autour des conditions dans `if` et `while`. Écrivez :

```julia
if a == b
```

au lieu de :

```julia
if (a == b)
```

## Don't overuse `...`

La fonction de découpage des arguments peut être addictive. Au lieu de `[a..., b...]`, utilisez simplement `[a; b]`, qui concatène déjà les tableaux. [`collect(a)`](@ref) est meilleur que `[a...]`, mais puisque `a` est déjà itérable, il est souvent encore mieux de le laisser tel quel et de ne pas le convertir en tableau.

## Ensure constructors return an instance of their own type

When a method `T(x)` is called on a type `T`, it is generally expected to return a value of type T. Defining a [constructor](@ref man-constructors) that returns an unexpected type can lead to confusing and unpredictable behavior:

```jldoctest
julia> struct Foo{T}
           x::T
       end

julia> Base.Float64(foo::Foo) = Foo(Float64(foo.x))  # Do not define methods like this

julia> Float64(Foo(3))  # Should return `Float64`
Foo{Float64}(3.0)

julia> Foo{Int}(x) = Foo{Float64}(x)  # Do not define methods like this

julia> Foo{Int}(3)  # Should return `Foo{Int}`
Foo{Float64}(3.0)
```

Pour maintenir la clarté du code et garantir la cohérence des types, concevez toujours les constructeurs pour qu'ils retournent une instance du type qu'ils sont censés construire.

## Don't use unnecessary static parameters

Une signature de fonction :

```julia
foo(x::T) where {T<:Real} = ...
```

devrait être écrit comme :

```julia
foo(x::Real) = ...
```

au lieu de cela, surtout si `T` n'est pas utilisé dans le corps de la fonction. Même si `T` est utilisé, il peut être remplacé par [`typeof(x)`](@ref) si cela est pratique. Il n'y a pas de différence de performance. Notez que ce n'est pas un avertissement général contre les paramètres statiques, mais simplement contre les utilisations où ils ne sont pas nécessaires.

Notez également que les types de conteneurs, en particulier, peuvent nécessiter des paramètres de type dans les appels de fonction. Consultez la FAQ [Avoid fields with abstract containers](@ref) pour plus d'informations.

## Avoid confusion about whether something is an instance or a type

Des ensembles de définitions comme les suivants sont déroutants :

```julia
foo(::Type{MyType}) = ...
foo(::MyType) = foo(MyType)
```

Décidez si le concept en question sera écrit comme `MyType` ou `MyType()`, et tenez-vous-en à cela.

Le style préféré est d'utiliser des instances par défaut, et d'ajouter uniquement des méthodes impliquant `Type{MyType}` plus tard si cela devient nécessaire pour résoudre certains problèmes.

Si un type est effectivement une énumération, il doit être défini comme un type unique (idéalement un struct ou un type primitif immuable), les valeurs de l'énumération étant des instances de celui-ci. Les constructeurs et les conversions peuvent vérifier si les valeurs sont valides. Ce design est préféré à celui qui consiste à faire de l'énumération un type abstrait, avec les "valeurs" comme sous-types.

## Don't overuse macros

Soyez conscient de quand un macro pourrait vraiment être une fonction à la place.

Appeler [`eval`](@ref) à l'intérieur d'une macro est un signe d'avertissement particulièrement dangereux ; cela signifie que la macro ne fonctionnera que lorsqu'elle est appelée au niveau supérieur. Si une telle macro est écrite comme une fonction à la place, elle aura naturellement accès aux valeurs d'exécution dont elle a besoin.

## Don't expose unsafe operations at the interface level

Si vous avez un type qui utilise un pointeur natif :

```julia
mutable struct NativeType
    p::Ptr{UInt8}
    ...
end
```

ne pas écrire de définitions comme celles-ci :

```julia
getindex(x::NativeType, i) = unsafe_load(x.p, i)
```

Le problème est que les utilisateurs de ce type peuvent écrire `x[i]` sans réaliser que l'opération est dangereuse, et peuvent alors être sujets à des bugs de mémoire.

Une telle fonction devrait soit vérifier l'opération pour s'assurer qu'elle est sûre, soit avoir `unsafe` quelque part dans son nom pour alerter les appelants.

## Don't overload methods of base container types

Il est possible d'écrire des définitions comme les suivantes :

```julia
show(io::IO, v::Vector{MyType}) = ...
```

Cela fournirait une présentation personnalisée des vecteurs avec un type d'élément nouveau spécifique. Bien que cela soit tentant, cela devrait être évité. Le problème est que les utilisateurs s'attendront à ce qu'un type bien connu comme `Vector()` se comporte d'une certaine manière, et une personnalisation excessive de son comportement peut rendre son utilisation plus difficile.

## [Avoid type piracy](@id avoid-type-piracy)

"Le piratage de type" fait référence à la pratique d'étendre ou de redéfinir des méthodes dans Base ou d'autres packages sur des types que vous n'avez pas définis. Dans des cas extrêmes, vous pouvez faire planter Julia (par exemple, si votre extension ou redéfinition de méthode entraîne le passage d'une entrée invalide à un `ccall`). Le piratage de type peut compliquer le raisonnement sur le code et peut introduire des incompatibilités difficiles à prévoir et à diagnostiquer.

Par exemple, supposons que vous souhaitiez définir la multiplication sur des symboles dans un module :

```julia
module A
import Base.*
*(x::Symbol, y::Symbol) = Symbol(x,y)
end
```

Le problème est que maintenant tout autre module qui utilise `Base.*` verra également cette définition. Étant donné que `Symbol` est défini dans Base et est utilisé par d'autres modules, cela peut modifier le comportement de code non lié de manière inattendue. Il existe plusieurs alternatives ici, y compris l'utilisation d'un nom de fonction différent ou l'encapsulation des `Symbol`s dans un autre type que vous définissez.

Parfois, des paquets couplés peuvent s'engager dans la piraterie de type pour séparer les fonctionnalités des définitions, en particulier lorsque les paquets ont été conçus par des auteurs collaborant, et lorsque les définitions sont réutilisables. Par exemple, un paquet pourrait fournir certains types utiles pour travailler avec les couleurs ; un autre paquet pourrait définir des méthodes pour ces types qui permettent des conversions entre les espaces colorimétriques. Un autre exemple pourrait être un paquet qui agit comme un mince wrapper pour du code C, que d'autres paquets pourraient ensuite pirater pour implémenter une API de niveau supérieur, conviviale avec Julia.

## Be careful with type equality

Vous voulez généralement utiliser [`isa`](@ref) et [`<:`](@ref) pour tester les types, pas `==`. Vérifier les types pour une égalité exacte n'a généralement de sens que lorsque vous comparez à un type concret connu (par exemple, `T == Float64`), ou si vous *savez vraiment, vraiment* ce que vous faites.

## Don't write a trivial anonymous function `x->f(x)` for a named function `f`

Puisque les fonctions d'ordre supérieur sont souvent appelées avec des fonctions anonymes, il est facile de conclure que cela est souhaitable ou même nécessaire. Mais toute fonction peut être passée directement, sans être "enveloppée" dans une fonction anonyme. Au lieu d'écrire `map(x->f(x), a)`, écrivez [`map(f, a)`](@ref).

## Avoid using floats for numeric literals in generic code when possible

Si vous écrivez du code générique qui gère des nombres et qui peut être attendu pour fonctionner avec de nombreux arguments de types numériques différents, essayez d'utiliser des littéraux d'un type numérique qui affectera les arguments le moins possible par le biais de la promotion.

Par exemple,

```jldoctest
julia> f(x) = 2.0 * x
f (generic function with 1 method)

julia> f(1//2)
1.0

julia> f(1/2)
1.0

julia> f(1)
2.0
```

tandis que

```jldoctest
julia> g(x) = 2 * x
g (generic function with 1 method)

julia> g(1//2)
1//1

julia> g(1/2)
1.0

julia> g(1)
2
```

Comme vous pouvez le voir, la deuxième version, où nous avons utilisé un littéral `Int`, a préservé le type de l'argument d'entrée, tandis que la première ne l'a pas fait. Cela est dû au fait que par exemple `promote_type(Int, Float64) == Float64`, et la promotion se produit avec la multiplication. De même, les littéraux [`Rational`](@ref) sont moins perturbateurs pour le type que les littéraux [`Float64`](@ref), mais plus perturbateurs que les `Int`s :

```jldoctest
julia> h(x) = 2//1 * x
h (generic function with 1 method)

julia> h(1//2)
1//1

julia> h(1/2)
1.0

julia> h(1)
2//1
```

Ainsi, utilisez des littéraux `Int` lorsque cela est possible, avec `Rational{Int}` pour les nombres non entiers littéraux, afin de faciliter l'utilisation de votre code.
