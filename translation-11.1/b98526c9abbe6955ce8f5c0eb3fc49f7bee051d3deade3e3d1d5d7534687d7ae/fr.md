# [Constructors](@id man-constructors)

Constructeurs [^1] sont des fonctions qui créent de nouveaux objets – spécifiquement, des instances de [Composite Types](@ref). En Julia, les objets de type servent également de fonctions de constructeur : ils créent de nouvelles instances d'eux-mêmes lorsqu'ils sont appliqués à un tuple d'arguments comme une fonction. Cela a déjà été mentionné brièvement lors de l'introduction des types composites. Par exemple :

```jldoctest footype
julia> struct Foo
           bar
           baz
       end

julia> foo = Foo(1, 2)
Foo(1, 2)

julia> foo.bar
1

julia> foo.baz
2
```

Pour de nombreux types, la formation de nouveaux objets en liant leurs valeurs de champ ensemble est tout ce qui est nécessaire pour créer des instances. Cependant, dans certains cas, plus de fonctionnalité est requise lors de la création d'objets composites. Parfois, des invariants doivent être respectés, soit en vérifiant les arguments, soit en les transformant. [Recursive data structures](https://en.wikipedia.org/wiki/Recursion_%28computer_science%29#Recursive_data_structures_.28structural_recursion.29), en particulier ceux qui peuvent être auto-référentiels, ne peuvent souvent pas être construits proprement sans d'abord être créés dans un état incomplet, puis modifiés par programmation pour être rendus entiers, comme une étape distincte de la création d'objet. Parfois, il est tout simplement pratique de pouvoir construire des objets avec moins ou différents types de paramètres que ceux qu'ils ont comme champs. Le système de Julia pour la construction d'objets aborde tous ces cas et plus encore.

[^1]: Nomenclature: while the term "constructor" generally refers to the entire function which constructs objects of a type, it is common to abuse terminology slightly and refer to specific constructor methods as "constructors". In such situations, it is generally clear from the context that the term is used to mean "constructor method" rather than "constructor function", especially as it is often used in the sense of singling out a particular method of the constructor from all of the others.

## [Outer Constructor Methods](@id man-outer-constructor-methods)

Un constructeur est comme n'importe quelle autre fonction en Julia en ce sens que son comportement global est défini par le comportement combiné de ses méthodes. En conséquence, vous pouvez ajouter des fonctionnalités à un constructeur en définissant simplement de nouvelles méthodes. Par exemple, disons que vous souhaitez ajouter une méthode de constructeur pour les objets `Foo` qui prend uniquement un argument et utilise la valeur donnée pour les champs `bar` et `baz`. C'est simple :

```jldoctest footype
julia> Foo(x) = Foo(x,x)
Foo

julia> Foo(1)
Foo(1, 1)
```

Vous pourriez également ajouter une méthode de constructeur `Foo` sans argument qui fournit des valeurs par défaut pour les deux champs `bar` et `baz` :

```jldoctest footype
julia> Foo() = Foo(0)
Foo

julia> Foo()
Foo(0, 0)
```

Ici, la méthode du constructeur sans argument appelle la méthode du constructeur avec un argument, qui à son tour appelle la méthode du constructeur à deux arguments fournie automatiquement. Pour des raisons qui deviendront claires très bientôt, les méthodes de constructeur supplémentaires déclarées comme des méthodes normales comme celle-ci sont appelées *méthodes de constructeur extérieures*. Les méthodes de constructeur extérieures ne peuvent créer une nouvelle instance qu'en appelant une autre méthode de constructeur, comme celles fournies par défaut.

## [Inner Constructor Methods](@id man-inner-constructor-methods)

Bien que les méthodes de constructeur externes réussissent à résoudre le problème de la fourniture de méthodes de commodité supplémentaires pour la construction d'objets, elles échouent à traiter les deux autres cas d'utilisation mentionnés dans l'introduction de ce chapitre : l'application des invariants et la possibilité de construire des objets auto-référentiels. Pour ces problèmes, il faut des méthodes de constructeur *internes*. Une méthode de constructeur interne est semblable à une méthode de constructeur externe, à deux différences près :

1. Il est déclaré à l'intérieur du bloc d'une déclaration de type, plutôt qu'à l'extérieur comme les méthodes normales.
2. Il a accès à une fonction spéciale localement existante appelée [`new`](@ref) qui crée des objets du type du bloc.

Par exemple, supposons que l'on veuille déclarer un type qui contient une paire de nombres réels, sous la contrainte que le premier nombre n'est pas supérieur au second. On pourrait le déclarer comme ceci :

```jldoctest pairtype
julia> struct OrderedPair
           x::Real
           y::Real
           OrderedPair(x,y) = x > y ? error("out of order") : new(x,y)
       end
```

Maintenant, les objets `OrderedPair` ne peuvent être construits que de manière à ce que `x <= y` :

```jldoctest pairtype; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> OrderedPair(1, 2)
OrderedPair(1, 2)

julia> OrderedPair(2,1)
ERROR: out of order
Stacktrace:
 [1] error at ./error.jl:33 [inlined]
 [2] OrderedPair(::Int64, ::Int64) at ./none:4
 [3] top-level scope
```

Si le type était déclaré `mutable`, vous pourriez accéder directement et modifier les valeurs des champs pour violer cet invariant. Bien sûr, fouiller dans les internals d'un objet sans y être invité est une mauvaise pratique. Vous (ou quelqu'un d'autre) pouvez également fournir des méthodes de constructeur externes supplémentaires à tout moment ultérieur, mais une fois qu'un type est déclaré, il n'y a aucun moyen d'ajouter d'autres méthodes de constructeur internes. Étant donné que les méthodes de constructeur externes ne peuvent créer des objets qu'en appelant d'autres méthodes de constructeur, en fin de compte, une méthode de constructeur interne doit être appelée pour créer un objet. Cela garantit que tous les objets du type déclaré doivent exister grâce à un appel à l'une des méthodes de constructeur internes fournies avec le type, donnant ainsi un certain degré d'application des invariants d'un type.

Si une méthode de constructeur interne est définie, aucune méthode de constructeur par défaut n'est fournie : on suppose que vous avez fourni vous-même tous les constructeurs internes dont vous avez besoin. Le constructeur par défaut équivaut à écrire votre propre méthode de constructeur interne qui prend tous les champs de l'objet comme paramètres (contraints d'être du bon type, si le champ correspondant a un type) et les passe à `new`, retournant l'objet résultant :

```jldoctest
julia> struct Foo
           bar
           baz
           Foo(bar,baz) = new(bar,baz)
       end

```

Cette déclaration a le même effet que la définition antérieure du type `Foo` sans méthode de constructeur interne explicite. Les deux types suivants sont équivalents – l'un avec un constructeur par défaut, l'autre avec un constructeur explicite :

```jldoctest
julia> struct T1
           x::Int64
       end

julia> struct T2
           x::Int64
           T2(x) = new(x)
       end

julia> T1(1)
T1(1)

julia> T2(1)
T2(1)

julia> T1(1.0)
T1(1)

julia> T2(1.0)
T2(1)
```

Il est bon de fournir aussi peu de méthodes de constructeur internes que possible : seulement celles prenant tous les arguments explicitement et imposant un contrôle d'erreur essentiel et une transformation. Des méthodes de constructeur de commodité supplémentaires, fournissant des valeurs par défaut ou des transformations auxiliaires, devraient être fournies en tant que constructeurs externes qui appellent les constructeurs internes pour effectuer le travail lourd. Cette séparation est généralement assez naturelle.

## Incomplete Initialization

Le problème final qui n'a toujours pas été abordé est la construction d'objets auto-référentiels, ou plus généralement, de structures de données récursives. Comme la difficulté fondamentale peut ne pas être immédiatement évidente, permettez-nous de l'expliquer brièvement. Considérons la déclaration de type récursive suivante :

```jldoctest selfrefer
julia> mutable struct SelfReferential
           obj::SelfReferential
       end

```

Ce type peut sembler inoffensif, jusqu'à ce qu'on considère comment en construire une instance. Si `a` est une instance de `SelfReferential`, alors une deuxième instance peut être créée par l'appel :

```julia-repl
julia> b = SelfReferential(a)
```

Mais comment construire la première instance lorsqu'aucune instance n'existe pour fournir une valeur valide pour son champ `obj` ? La seule solution est de permettre la création d'une instance incomplètement initialisée de `SelfReferential` avec un champ `obj` non assigné, et d'utiliser cette instance incomplète comme une valeur valide pour le champ `obj` d'une autre instance, comme, par exemple, elle-même.

Pour permettre la création d'objets incomplètement initialisés, Julia permet d'appeler la fonction [`new`](@ref) avec moins de champs que le type n'en a, retournant un objet avec les champs non spécifiés non initialisés. La méthode du constructeur interne peut ensuite utiliser l'objet incomplet, terminant son initialisation avant de le retourner. Ici, par exemple, voici une autre tentative de définition du type `SelfReferential`, cette fois en utilisant un constructeur interne sans argument retournant des instances ayant des champs `obj` pointant vers elles-mêmes :

```jldoctest selfrefer2
julia> mutable struct SelfReferential
           obj::SelfReferential
           SelfReferential() = (x = new(); x.obj = x)
       end

```

Nous pouvons vérifier que ce constructeur fonctionne et construit des objets qui sont, en fait, auto-référentiels :

```jldoctest selfrefer2
julia> x = SelfReferential();

julia> x === x
true

julia> x === x.obj
true

julia> x === x.obj.obj
true
```

Bien qu'il soit généralement préférable de retourner un objet entièrement initialisé depuis un constructeur interne, il est possible de retourner des objets partiellement initialisés :

```jldoctest incomplete
julia> mutable struct Incomplete
           data
           Incomplete() = new()
       end

julia> z = Incomplete();
```

Bien que vous soyez autorisé à créer des objets avec des champs non initialisés, tout accès à une référence non initialisée est une erreur immédiate :

```jldoctest incomplete
julia> z.data
ERROR: UndefRefError: access to undefined reference
```

Cela évite la nécessité de vérifier continuellement les valeurs `null`. Cependant, tous les champs d'objet ne sont pas des références. Julia considère certains types comme des "données simples", ce qui signifie que toutes leurs données sont auto-contenues et ne font pas référence à d'autres objets. Les types de données simples se composent de types primitifs (par exemple, `Int`) et de structures immuables d'autres types de données simples (voir aussi : [`isbits`](@ref), [`isbitstype`](@ref)). Le contenu initial d'un type de données simples est indéfini :

```julia-repl
julia> struct HasPlain
           n::Int
           HasPlain() = new()
       end

julia> HasPlain()
HasPlain(438103441441)
```

Les tableaux de types de données simples présentent le même comportement.

Vous pouvez passer des objets incomplets à d'autres fonctions depuis des constructeurs internes pour déléguer leur achèvement :

```jldoctest
julia> mutable struct Lazy
           data
           Lazy(v) = complete_me(new(), v)
       end
```

Comme avec les objets incomplets retournés par les constructeurs, si `complete_me` ou l'un de ses appelants essaie d'accéder au champ `data` de l'objet `Lazy` avant qu'il n'ait été initialisé, une erreur sera immédiatement déclenchée.

## Parametric Constructors

Parametric types add a few wrinkles to the constructor story. Recall from [Parametric Types](@ref) that, by default, instances of parametric composite types can be constructed either with explicitly given type parameters or with type parameters implied by the types of the arguments given to the constructor. Here are some examples:

```jldoctest parametric; filter = r"Closest candidates.*\n  .*"
julia> struct Point{T<:Real}
           x::T
           y::T
       end

julia> Point(1,2) ## implicit T ##
Point{Int64}(1, 2)

julia> Point(1.0,2.5) ## implicit T ##
Point{Float64}(1.0, 2.5)

julia> Point(1,2.5) ## implicit T ##
ERROR: MethodError: no method matching Point(::Int64, ::Float64)
The type `Point` exists, but no method is defined for this combination of argument types when trying to construct it.

Closest candidates are:
  Point(::T, ::T) where T<:Real at none:2

julia> Point{Int64}(1, 2) ## explicit T ##
Point{Int64}(1, 2)

julia> Point{Int64}(1.0,2.5) ## explicit T ##
ERROR: InexactError: Int64(2.5)
Stacktrace:
[...]

julia> Point{Float64}(1.0, 2.5) ## explicit T ##
Point{Float64}(1.0, 2.5)

julia> Point{Float64}(1,2) ## explicit T ##
Point{Float64}(1.0, 2.0)
```

Comme vous pouvez le voir, pour les appels de constructeur avec des paramètres de type explicites, les arguments sont convertis aux types de champ implicites : `Point{Int64}(1,2)` fonctionne, mais `Point{Int64}(1.0,2.5)` soulève une [`InexactError`](@ref) lors de la conversion de `2.5` en [`Int64`](@ref). Lorsque le type est implicite par les arguments de l'appel du constructeur, comme dans `Point(1,2)`, alors les types des arguments doivent être compatibles – sinon le `T` ne peut pas être déterminé – mais n'importe quelle paire d'arguments réels avec un type correspondant peut être donnée au constructeur générique `Point`.

Ce qui se passe vraiment ici, c'est que `Point`, `Point{Float64}` et `Point{Int64}` sont tous des fonctions de constructeur différentes. En fait, `Point{T}` est une fonction de constructeur distincte pour chaque type `T`. Sans aucun constructeur interne explicitement fourni, la déclaration du type composite `Point{T<:Real}` fournit automatiquement un constructeur interne, `Point{T}`, pour chaque type possible `T<:Real`, qui se comporte exactement comme le font les constructeurs internes par défaut non paramétriques. Elle fournit également un unique constructeur externe général `Point` qui prend des paires d'arguments réels, qui doivent être du même type. Cette fourniture automatique de constructeurs est équivalente à la déclaration explicite suivante :

```jldoctest parametric2
julia> struct Point{T<:Real}
           x::T
           y::T
           Point{T}(x,y) where {T<:Real} = new(x,y)
       end

julia> Point(x::T, y::T) where {T<:Real} = Point{T}(x,y);
```

Remarquez que chaque définition ressemble à la forme d'appel de constructeur qu'elle gère. L'appel `Point{Int64}(1,2)` invoquera la définition `Point{T}(x,y)` à l'intérieur du bloc `struct`. La déclaration de constructeur externe, en revanche, définit une méthode pour le constructeur général `Point` qui ne s'applique qu'aux paires de valeurs du même type réel. Cette déclaration permet aux appels de constructeur sans paramètres de type explicites, comme `Point(1,2)` et `Point(1.0,2.5)`, de fonctionner. Étant donné que la déclaration de méthode restreint les arguments à être du même type, des appels comme `Point(1,2.5)`, avec des arguments de types différents, entraînent des erreurs "aucune méthode".

Supposons que nous voulions faire en sorte que l'appel au constructeur `Point(1,2.5)` fonctionne en "promouvant" la valeur entière `1` à la valeur flottante `1.0`. La manière la plus simple d'y parvenir est de définir la méthode de constructeur externe suivante :

```jldoctest parametric2
julia> Point(x::Int64, y::Float64) = Point(convert(Float64,x),y);
```

Cette méthode utilise la fonction [`convert`](@ref) pour convertir explicitement `x` en [`Float64`](@ref) et délègue ensuite la construction au constructeur général pour le cas où les deux arguments sont `4d61726b646f776e2e436f64652822222c2022466c6f617436342229_40726566`. Avec cette définition de méthode, ce qui était auparavant un [`MethodError`](@ref) crée maintenant avec succès un point de type `Point{Float64}` :

```jldoctest parametric2
julia> p = Point(1,2.5)
Point{Float64}(1.0, 2.5)

julia> typeof(p)
Point{Float64}
```

Cependant, d'autres appels similaires ne fonctionnent toujours pas :

```jldoctest parametric2
julia> Point(1.5,2)
ERROR: MethodError: no method matching Point(::Float64, ::Int64)
The type `Point` exists, but no method is defined for this combination of argument types when trying to construct it.

Closest candidates are:
  Point(::T, !Matched::T) where T<:Real
   @ Main none:1
  Point(!Matched::Int64, !Matched::Float64)
   @ Main none:1

Stacktrace:
[...]
```

For a more general way to make all such calls work sensibly, see [Conversion and Promotion](@ref conversion-and-promotion). At the risk of spoiling the suspense, we can reveal here that all it takes is the following outer method definition to make all calls to the general `Point` constructor work as one would expect:

```jldoctest parametric2
julia> Point(x::Real, y::Real) = Point(promote(x,y)...);
```

La fonction `promote` convertit tous ses arguments en un type commun – dans ce cas [`Float64`](@ref). Avec cette définition de méthode, le constructeur `Point` promeut ses arguments de la même manière que les opérateurs numériques comme [`+`](@ref) le font, et fonctionne pour tous les types de nombres réels :

```jldoctest parametric2
julia> Point(1.5,2)
Point{Float64}(1.5, 2.0)

julia> Point(1,1//2)
Point{Rational{Int64}}(1//1, 1//2)

julia> Point(1.0,1//2)
Point{Float64}(1.0, 0.5)
```

Ainsi, bien que les constructeurs de paramètres de type implicites fournis par défaut dans Julia soient assez stricts, il est possible de les faire fonctionner de manière plus détendue mais sensée assez facilement. De plus, puisque les constructeurs peuvent tirer parti de toute la puissance du système de types, des méthodes et du dispatch multiple, définir un comportement sophistiqué est généralement assez simple.

## Case Study: Rational

Peut-être que la meilleure façon de rassembler tous ces éléments est de présenter un exemple concret d'un type composite paramétrique et de ses méthodes de constructeur. À cette fin, nous implémentons notre propre type de nombre rationnel `OurRational`, similaire au type intégré de Julia [`Rational`](@ref), défini dans [`rational.jl`](https://github.com/JuliaLang/julia/blob/master/base/rational.jl) :

```jldoctest rational
julia> struct OurRational{T<:Integer} <: Real
           num::T
           den::T
           function OurRational{T}(num::T, den::T) where T<:Integer
               if num == 0 && den == 0
                    error("invalid rational: 0//0")
               end
               num = flipsign(num, den)
               den = flipsign(den, den)
               g = gcd(num, den)
               num = div(num, g)
               den = div(den, g)
               new(num, den)
           end
       end

julia> OurRational(n::T, d::T) where {T<:Integer} = OurRational{T}(n,d)
OurRational

julia> OurRational(n::Integer, d::Integer) = OurRational(promote(n,d)...)
OurRational

julia> OurRational(n::Integer) = OurRational(n,one(n))
OurRational

julia> ⊘(n::Integer, d::Integer) = OurRational(n,d)
⊘ (generic function with 1 method)

julia> ⊘(x::OurRational, y::Integer) = x.num ⊘ (x.den*y)
⊘ (generic function with 2 methods)

julia> ⊘(x::Integer, y::OurRational) = (x*y.den) ⊘ y.num
⊘ (generic function with 3 methods)

julia> ⊘(x::Complex, y::Real) = complex(real(x) ⊘ y, imag(x) ⊘ y)
⊘ (generic function with 4 methods)

julia> ⊘(x::Real, y::Complex) = (x*y') ⊘ real(y*y')
⊘ (generic function with 5 methods)

julia> function ⊘(x::Complex, y::Complex)
           xy = x*y'
           yy = real(y*y')
           complex(real(xy) ⊘ yy, imag(xy) ⊘ yy)
       end
⊘ (generic function with 6 methods)
```

La première ligne – `struct OurRational{T<:Integer} <: Real` – déclare que `OurRational` prend un paramètre de type d'un type entier, et est lui-même un type réel. Les déclarations de champ `num::T` et `den::T` indiquent que les données contenues dans un objet `OurRational{T}` sont une paire d'entiers de type `T`, l'un représentant le numérateur de la valeur rationnelle et l'autre représentant son dénominateur.

Maintenant, les choses deviennent intéressantes. `OurRational` a une seule méthode de constructeur interne qui vérifie que `num` et `den` ne sont pas tous deux nuls et garantit que chaque rationnel est construit en "termes les plus bas" avec un dénominateur non négatif. Cela est accompli en inversant d'abord les signes du numérateur et du dénominateur si le dénominateur est négatif. Ensuite, les deux sont divisés par leur plus grand commun diviseur (`gcd` renvoie toujours un nombre non négatif, quelle que soit la signe de ses arguments). Comme c'est le seul constructeur interne pour `OurRational`, nous pouvons être certains que les objets `OurRational` sont toujours construits sous cette forme normalisée.

`OurRational` fournit également plusieurs méthodes de constructeur externes pour plus de commodité. La première est le "constructeur général standard" qui infère le paramètre de type `T` à partir du type du numérateur et du dénominateur lorsqu'ils ont le même type. La seconde s'applique lorsque les valeurs de numérateur et de dénominateur données ont des types différents : elle les promeut à un type commun et délègue ensuite la construction au constructeur externe pour des arguments de type correspondant. Le troisième constructeur externe transforme les valeurs entières en rationnels en fournissant une valeur de `1` comme dénominateur.

En suivant les définitions des constructeurs externes, nous avons défini un certain nombre de méthodes pour l'opérateur `⊘`, qui fournit une syntaxe pour écrire des rationnels (par exemple, `1 ⊘ 2`). Le type `Rational` de Julia utilise l'opérateur [`//`](@ref) à cet effet. Avant ces définitions, `⊘` est un opérateur complètement indéfini avec seulement une syntaxe et pas de signification. Par la suite, il se comporte exactement comme décrit dans [Rational Numbers](@ref) – son comportement entier est défini dans ces quelques lignes. Notez que l'utilisation infixe de `⊘` fonctionne parce que Julia a un ensemble de symboles qui sont reconnus comme des opérateurs infixes. La première et la plus basique des définitions fait que `a ⊘ b` construit un `OurRational` en appliquant le constructeur `OurRational` à `a` et `b` lorsqu'ils sont des entiers. Lorsque l'un des opérandes de `⊘` est déjà un nombre rationnel, nous construisons un nouveau rationnel pour le rapport résultant légèrement différemment ; ce comportement est en fait identique à la division d'un rationnel par un entier. Enfin, appliquer `⊘` à des valeurs entières complexes crée une instance de `Complex{<:OurRational}` – un nombre complexe dont les parties réelle et imaginaire sont des rationnels :

```jldoctest rational
julia> z = (1 + 2im) ⊘ (1 - 2im);

julia> typeof(z)
Complex{OurRational{Int64}}

julia> typeof(z) <: Complex{<:OurRational}
true
```

Ainsi, bien que l'opérateur `⊘` renvoie généralement une instance de `OurRational`, s'il y a des entiers complexes parmi ses arguments, il renverra plutôt une instance de `Complex{<:OurRational}`. Le lecteur intéressé devrait envisager de parcourir le reste de [`rational.jl`](https://github.com/JuliaLang/julia/blob/master/base/rational.jl): c'est court, autonome et implémente un type Julia de base entier.

## Outer-only constructors

Comme nous l'avons vu, un type paramétrique typique a des constructeurs internes qui sont appelés lorsque les paramètres de type sont connus ; par exemple, ils s'appliquent à `Point{Int}` mais pas à `Point`. En option, des constructeurs externes qui déterminent automatiquement les paramètres de type peuvent être ajoutés, par exemple en construisant un `Point{Int}` à partir de l'appel `Point(1,2)`. Les constructeurs externes appellent les constructeurs internes pour créer effectivement des instances. Cependant, dans certains cas, on préférerait ne pas fournir de constructeurs internes, de sorte que des paramètres de type spécifiques ne puissent pas être demandés manuellement.

Par exemple, disons que nous définissons un type qui stocke un vecteur avec une représentation précise de sa somme :

```jldoctest
julia> struct SummedArray{T<:Number,S<:Number}
           data::Vector{T}
           sum::S
       end

julia> SummedArray(Int32[1; 2; 3], Int32(6))
SummedArray{Int32, Int32}(Int32[1, 2, 3], 6)
```

Le problème est que nous voulons que `S` soit un type plus grand que `T`, afin que nous puissions additionner de nombreux éléments avec moins de perte d'information. Par exemple, lorsque `T` est [`Int32`](@ref), nous aimerions que `S` soit [`Int64`](@ref). Par conséquent, nous voulons éviter une interface qui permet à l'utilisateur de construire des instances du type `SummedArray{Int32,Int32}`. Une façon de le faire est de fournir un constructeur uniquement pour `SummedArray`, mais à l'intérieur du bloc de définition de `struct`, de supprimer la génération de constructeurs par défaut :

```jldoctest
julia> struct SummedArray{T<:Number,S<:Number}
           data::Vector{T}
           sum::S
           function SummedArray(a::Vector{T}) where T
               S = widen(T)
               new{T,S}(a, sum(S, a))
           end
       end

julia> SummedArray(Int32[1; 2; 3], Int32(6))
ERROR: MethodError: no method matching SummedArray(::Vector{Int32}, ::Int32)
The type `SummedArray` exists, but no method is defined for this combination of argument types when trying to construct it.

Closest candidates are:
  SummedArray(::Vector{T}) where T
   @ Main none:4

Stacktrace:
[...]
```

Ce constructeur sera invoqué par la syntaxe `SummedArray(a)`. La syntaxe `new{T,S}` permet de spécifier des paramètres pour le type à construire, c'est-à-dire que cet appel renverra un `SummedArray{T,S}`. `new{T,S}` peut être utilisé dans toute définition de constructeur, mais par commodité, les paramètres de `new{}` sont automatiquement dérivés du type en cours de construction lorsque cela est possible.

## Constructors are just callable objects

Un objet de n'importe quel type peut être [made callable](@ref "Function-like objects") en définissant une méthode. Cela inclut les types, c'est-à-dire les objets de type [`Type`](@ref); et les constructeurs peuvent, en fait, être considérés comme de simples objets de type appelables. Par exemple, il existe de nombreuses méthodes définies sur `Bool` et divers supertypes de celui-ci :

```julia-repl
julia> methods(Bool)
# 10 methods for type constructor:
  [1] Bool(x::BigFloat)
     @ Base.MPFR mpfr.jl:393
  [2] Bool(x::Float16)
     @ Base float.jl:338
  [3] Bool(x::Rational)
     @ Base rational.jl:138
  [4] Bool(x::Real)
     @ Base float.jl:233
  [5] (dt::Type{<:Integer})(ip::Sockets.IPAddr)
     @ Sockets ~/tmp/jl/jl/julia-nightly-assert/share/julia/stdlib/v1.11/Sockets/src/IPAddr.jl:11
  [6] (::Type{T})(x::Enum{T2}) where {T<:Integer, T2<:Integer}
     @ Base.Enums Enums.jl:19
  [7] (::Type{T})(z::Complex) where T<:Real
     @ Base complex.jl:44
  [8] (::Type{T})(x::Base.TwicePrecision) where T<:Number
     @ Base twiceprecision.jl:265
  [9] (::Type{T})(x::T) where T<:Number
     @ boot.jl:894
 [10] (::Type{T})(x::AbstractChar) where T<:Union{AbstractChar, Number}
     @ char.jl:50
```

La syntaxe habituelle du constructeur est exactement équivalente à la syntaxe d'objet de type fonction, donc essayer de définir une méthode avec chaque syntaxe entraînera l'écrasement de la première méthode par la suivante :

```jldoctest
julia> struct S
           f::Int
       end

julia> S() = S(7)
S

julia> (::Type{S})() = S(8)  # overwrites the previous constructor method

julia> S()
S(8)
```
