# [Conversion and Promotion](@id conversion-and-promotion)

Julia a un système pour promouvoir les arguments des opérateurs mathématiques à un type commun, qui a été mentionné dans diverses autres sections, y compris [Integers and Floating-Point Numbers](@ref), [Mathematical Operations and Elementary Functions](@ref), [Types](@ref man-types), et [Methods](@ref). Dans cette section, nous expliquons comment fonctionne ce système de promotion, ainsi que comment l'étendre à de nouveaux types et l'appliquer à des fonctions en plus des opérateurs mathématiques intégrés. Traditionnellement, les langages de programmation se divisent en deux camps en ce qui concerne la promotion des arguments arithmétiques :

  * **Promotion automatique pour les types arithmétiques intégrés et les opérateurs.** Dans la plupart des langages, les types numériques intégrés, lorsqu'ils sont utilisés comme opérandes pour des opérateurs arithmétiques avec une syntaxe infixe, tels que `+`, `-`, `*` et `/`, sont automatiquement promus à un type commun pour produire les résultats attendus. C, Java, Perl et Python, pour n'en nommer que quelques-uns, calculent correctement la somme `1 + 1.5` comme la valeur à virgule flottante `2.5`, même si l'un des opérandes de `+` est un entier. Ces systèmes sont pratiques et conçus de manière suffisamment soignée pour qu'ils soient généralement presque invisibles pour le programmeur : presque personne ne pense consciemment à cette promotion lorsqu'il écrit une telle expression, mais les compilateurs et les interprètes doivent effectuer une conversion avant l'addition puisque les entiers et les valeurs à virgule flottante ne peuvent pas être ajoutés tels quels. Des règles complexes pour de telles conversions automatiques font donc inévitablement partie des spécifications et des implémentations de ces langages.
  * **Pas de promotion automatique.** Ce camp inclut Ada et ML – des langages à typage statique très "strict". Dans ces langages, chaque conversion doit être spécifiquement indiquée par le programmeur. Ainsi, l'expression exemple `1 + 1.5` provoquerait une erreur de compilation à la fois en Ada et en ML. Au lieu de cela, il faut écrire `real(1) + 1.5`, convertissant explicitement l'entier `1` en une valeur à virgule flottante avant d'effectuer l'addition. La conversion explicite partout est cependant si peu pratique, qu même Ada a un certain degré de conversion automatique : les littéraux entiers sont promus au type entier attendu automatiquement, et les littéraux à virgule flottante sont également promus aux types à virgule flottante appropriés.

Dans un sens, Julia tombe dans la catégorie "pas de promotion automatique" : les opérateurs mathématiques ne sont que des fonctions avec une syntaxe spéciale, et les arguments des fonctions ne sont jamais convertis automatiquement. Cependant, on peut observer que l'application d'opérations mathématiques à une grande variété de types d'arguments mixtes n'est qu'un cas extrême de dispatch multiple polymorphe – quelque chose que les systèmes de dispatch et de types de Julia sont particulièrement bien adaptés à gérer. La promotion "automatique" des opérandes mathématiques émerge simplement comme une application spéciale : Julia est livrée avec des règles de dispatch pré-définies qui attrapent tout pour les opérateurs mathématiques, invoquées lorsqu'aucune implémentation spécifique n'existe pour une certaine combinaison de types d'opérandes. Ces règles de capture d'exception promeuvent d'abord tous les opérandes à un type commun en utilisant des règles de promotion définies par l'utilisateur, puis invoquent une implémentation spécialisée de l'opérateur en question pour les valeurs résultantes, désormais du même type. Les types définis par l'utilisateur peuvent facilement participer à ce système de promotion en définissant des méthodes pour la conversion vers et depuis d'autres types, et en fournissant une poignée de règles de promotion définissant quels types ils devraient promouvoir lorsqu'ils sont mélangés avec d'autres types.

## Conversion

La manière standard d'obtenir une valeur d'un certain type `T` est d'appeler le constructeur du type, `T(x)`. Cependant, il existe des cas où il est pratique de convertir une valeur d'un type à un autre sans que le programmeur ne le demande explicitement. Un exemple est l'attribution d'une valeur dans un tableau : si `A` est un `Vector{Float64}`, l'expression `A[1] = 2` devrait fonctionner en convertissant automatiquement le `2` de `Int` en `Float64`, et en stockant le résultat dans le tableau. Cela se fait via la fonction [`convert`](@ref).

La fonction `convert` prend généralement deux arguments : le premier est un objet de type et le second est une valeur à convertir en ce type. La valeur retournée est la valeur convertie en une instance du type donné. La manière la plus simple de comprendre cette fonction est de la voir en action :

```jldoctest
julia> x = 12
12

julia> typeof(x)
Int64

julia> xu = convert(UInt8, x)
0x0c

julia> typeof(xu)
UInt8

julia> xf = convert(AbstractFloat, x)
12.0

julia> typeof(xf)
Float64

julia> a = Any[1 2 3; 4 5 6]
2×3 Matrix{Any}:
 1  2  3
 4  5  6

julia> convert(Array{Float64}, a)
2×3 Matrix{Float64}:
 1.0  2.0  3.0
 4.0  5.0  6.0
```

La conversion n'est pas toujours possible, auquel cas un [`MethodError`](@ref) est lancé indiquant que `convert` ne sait pas comment effectuer la conversion demandée :

```jldoctest
julia> convert(AbstractFloat, "foo")
ERROR: MethodError: Cannot `convert` an object of type String to an object of type AbstractFloat
[...]
```

Certaines langues considèrent que l'analyse de chaînes en tant que nombres ou le formatage de nombres en tant que chaînes est une conversion (de nombreuses langues dynamiques effectueront même la conversion automatiquement pour vous). Ce n'est pas le cas en Julia. Même si certaines chaînes peuvent être analysées en tant que nombres, la plupart des chaînes ne sont pas des représentations valides de nombres, et seulement un sous-ensemble très limité d'entre elles l'est. Par conséquent, en Julia, la fonction dédiée [`parse`](@ref) doit être utilisée pour effectuer cette opération, la rendant plus explicite.

### When is `convert` called?

Les constructions de langage suivantes appellent `convert` :

  * L'assignation à un tableau se convertit au type d'élément du tableau.
  * L'assignation à un champ d'un objet se convertit au type déclaré du champ.
  * Construire un objet avec [`new`](@ref) se convertit en les types de champs déclarés de l'objet.
  * L'assignation à une variable avec un type déclaré (par exemple, `local x::T`) se convertit en ce type.
  * Une fonction avec un type de retour déclaré convertit sa valeur de retour en ce type.
  * Passer une valeur à [`ccall`](@ref) la convertit en le type d'argument correspondant.

### Conversion vs. Construction

Notez que le comportement de `convert(T, x)` semble presque identique à `T(x)`. En effet, c'est généralement le cas. Cependant, il existe une différence sémantique clé : puisque `convert` peut être appelé implicitement, ses méthodes sont limitées aux cas considérés comme "sûrs" ou "non surprenants". `convert` ne convertira que des types qui représentent le même type fondamental de chose (par exemple, différentes représentations de nombres ou différents encodages de chaînes). Il est également généralement sans perte ; convertir une valeur dans un type différent et revenir à l'original devrait donner exactement la même valeur.

Il existe quatre types généraux de cas où les constructeurs diffèrent de `convert` :

#### Constructors for types unrelated to their arguments

Certains constructeurs n'implémentent pas le concept de "conversion". Par exemple, `Timer(2)` crée un minuteur de 2 secondes, ce qui n'est pas vraiment une "conversion" d'un entier en minuteur.

#### Mutable collections

`convert(T, x)` est censé retourner l'original `x` si `x` est déjà de type `T`. En revanche, si `T` est un type de collection mutable, alors `T(x)` devrait toujours créer une nouvelle collection (en copiant les éléments de `x`).

#### Wrapper types

Pour certains types qui "enveloppent" d'autres valeurs, le constructeur peut envelopper son argument à l'intérieur d'un nouvel objet même s'il est déjà du type demandé. Par exemple, `Some(x)` enveloppe `x` pour indiquer qu'une valeur est présente (dans un contexte où le résultat pourrait être un `Some` ou `nothing`). Cependant, `x` lui-même pourrait être l'objet `Some(y)`, auquel cas le résultat est `Some(Some(y))`, avec deux niveaux d'enveloppement. `convert(Some, x)`, en revanche, renverrait simplement `x` puisqu'il est déjà un `Some`.

#### Constructors that don't return instances of their own type

Dans des cas *très rares*, il peut être logique que le constructeur `T(x)` retourne un objet qui n'est pas de type `T`. Cela pourrait se produire si un type d'enveloppe est son propre inverse (par exemple, `Flip(Flip(x)) === x`), ou pour prendre en charge une ancienne syntaxe d'appel pour la compatibilité ascendante lors de la restructuration d'une bibliothèque. Mais `convert(T, x)` devrait toujours retourner une valeur de type `T`.

### Defining New Conversions

Lors de la définition d'un nouveau type, toutes les manières de le créer doivent d'abord être définies comme des constructeurs. S'il devient clair qu'une conversion implicite serait utile, et que certains constructeurs répondent aux critères de "sécurité" ci-dessus, alors des méthodes `convert` peuvent être ajoutées. Ces méthodes sont généralement assez simples, car elles n'ont besoin que d'appeler le constructeur approprié. Une telle définition pourrait ressembler à ceci :

```julia
import Base: convert
convert(::Type{MyType}, x) = MyType(x)
```

Le type du premier argument de cette méthode est [`Type{MyType}`](@ref man-typet-type), dont la seule instance est `MyType`. Ainsi, cette méthode n'est invoquée que lorsque le premier argument est la valeur de type `MyType`. Remarquez la syntaxe utilisée pour le premier argument : le nom de l'argument est omis avant le symbole `::`, et seul le type est donné. C'est la syntaxe en Julia pour un argument de fonction dont le type est spécifié mais dont la valeur n'a pas besoin d'être référencée par son nom.

Toutes les instances de certains types abstraits sont par défaut considérées comme "suffisamment similaires" qu'une définition universelle de `convert` est fournie dans Julia Base. Par exemple, cette définition indique qu'il est valide de `convert` n'importe quel type `Number` en n'importe quel autre en appelant un constructeur à 1 argument :

```julia
convert(::Type{T}, x::Number) where {T<:Number} = T(x)::T
```

Cela signifie que les nouveaux types `Number` n'ont besoin de définir que des constructeurs, car cette définition gérera `convert` pour eux. Une conversion d'identité est également fournie pour gérer le cas où l'argument est déjà du type demandé :

```julia
convert(::Type{T}, x::T) where {T<:Number} = x
```

Des définitions similaires existent pour `AbstractString`, [`AbstractArray`](@ref), et [`AbstractDict`](@ref).

## Promotion

La promotion fait référence à la conversion de valeurs de types mixtes en un type commun unique. Bien que cela ne soit pas strictement nécessaire, il est généralement sous-entendu que le type commun vers lequel les valeurs sont converties peut représenter fidèlement toutes les valeurs d'origine. En ce sens, le terme "promotion" est approprié puisque les valeurs sont converties en un type "supérieur" – c'est-à-dire un type qui peut représenter toutes les valeurs d'entrée en un seul type commun. Il est cependant important de ne pas confondre cela avec le super-typage orienté objet (structurel), ou la notion de super-types abstraits de Julia : la promotion n'a rien à voir avec la hiérarchie des types, et tout à voir avec la conversion entre des représentations alternatives. Par exemple, bien que chaque valeur [`Int32`](@ref) puisse également être représentée comme une valeur [`Float64`](@ref), `Int32` n'est pas un sous-type de `Float64`.

La promotion vers un type "supérieur" commun est effectuée en Julia par la fonction [`promote`](@ref), qui prend un nombre quelconque d'arguments et retourne un tuple du même nombre de valeurs, converties en un type commun, ou lance une exception si la promotion n'est pas possible. Le cas d'utilisation le plus courant pour la promotion est de convertir des arguments numériques en un type commun :

```jldoctest
julia> promote(1, 2.5)
(1.0, 2.5)

julia> promote(1, 2.5, 3)
(1.0, 2.5, 3.0)

julia> promote(2, 3//4)
(2//1, 3//4)

julia> promote(1, 2.5, 3, 3//4)
(1.0, 2.5, 3.0, 0.75)

julia> promote(1.5, im)
(1.5 + 0.0im, 0.0 + 1.0im)

julia> promote(1 + 2im, 3//4)
(1//1 + 2//1*im, 3//4 + 0//1*im)
```

Les valeurs à virgule flottante sont promues au plus grand des types d'arguments à virgule flottante. Les valeurs entières sont promues au plus grand des types d'arguments entiers. Si les types ont la même taille mais diffèrent par leur signe, le type non signé est choisi. Les mélanges d'entiers et de valeurs à virgule flottante sont promus à un type à virgule flottante suffisamment grand pour contenir toutes les valeurs. Les entiers mélangés avec des rationnels sont promus à des rationnels. Les rationnels mélangés avec des flottants sont promus à des flottants. Les valeurs complexes mélangées avec des valeurs réelles sont promues au type approprié de valeur complexe.

C'est vraiment tout ce qu'il y a à savoir sur l'utilisation des promotions. Le reste n'est qu'une question d'application astucieuse, l'application "astucieuse" la plus typique étant la définition de méthodes générales pour les opérations numériques comme les opérateurs arithmétiques `+`, `-`, `*` et `/`. Voici quelques-unes des définitions de méthodes générales données dans [`promotion.jl`](https://github.com/JuliaLang/julia/blob/master/base/promotion.jl) :

```julia
+(x::Number, y::Number) = +(promote(x,y)...)
-(x::Number, y::Number) = -(promote(x,y)...)
*(x::Number, y::Number) = *(promote(x,y)...)
/(x::Number, y::Number) = /(promote(x,y)...)
```

Ces définitions de méthode indiquent qu'en l'absence de règles plus spécifiques pour l'addition, la soustraction, la multiplication et la division de paires de valeurs numériques, il faut promouvoir les valeurs à un type commun, puis réessayer. C'est tout : nulle part ailleurs il n'est jamais nécessaire de se soucier de la promotion à un type numérique commun pour les opérations arithmétiques – cela se produit automatiquement. Il existe des définitions de méthodes de promotion générales pour un certain nombre d'autres fonctions arithmétiques et mathématiques dans [`promotion.jl`](https://github.com/JuliaLang/julia/blob/master/base/promotion.jl), mais au-delà de cela, il y a à peine des appels à `promote` nécessaires dans Julia Base. Les usages les plus courants de `promote` se produisent dans les méthodes de constructeurs externes, fournies par commodité, pour permettre aux appels de constructeurs avec des types mixtes de déléguer à un type interne avec des champs promus à un type commun approprié. Par exemple, rappelez-vous que [`rational.jl`](https://github.com/JuliaLang/julia/blob/master/base/rational.jl) fournit la méthode de constructeur externe suivante :

```julia
Rational(n::Integer, d::Integer) = Rational(promote(n,d)...)
```

Cela permet à des appels comme les suivants de fonctionner :

```jldoctest
julia> x = Rational(Int8(15),Int32(-5))
-3//1

julia> typeof(x)
Rational{Int32}
```

Pour la plupart des types définis par l'utilisateur, il est préférable d'exiger des programmeurs qu'ils fournissent explicitement les types attendus aux fonctions de constructeur, mais parfois, en particulier pour les problèmes numériques, il peut être pratique de faire la promotion automatiquement.

### Defining Promotion Rules

Bien qu'on puisse, en principe, définir des méthodes pour la fonction `promote` directement, cela nécessiterait de nombreuses définitions redondantes pour toutes les permutations possibles des types d'arguments. Au lieu de cela, le comportement de `promote` est défini en termes d'une fonction auxiliaire appelée [`promote_rule`](@ref), pour laquelle on peut fournir des méthodes. La fonction `promote_rule` prend une paire d'objets de type et renvoie un autre objet de type, de sorte que les instances des types d'arguments seront promues au type retourné. Ainsi, en définissant la règle :

```julia
import Base: promote_rule
promote_rule(::Type{Float64}, ::Type{Float32}) = Float64
```

on déclare que lorsque des valeurs flottantes de 64 bits et de 32 bits sont promues ensemble, elles doivent être promues en flottant de 64 bits. Le type de promotion n'a pas besoin d'être l'un des types d'argument. Par exemple, les règles de promotion suivantes se produisent toutes deux dans Julia Base :

```julia
promote_rule(::Type{BigInt}, ::Type{Float64}) = BigFloat
promote_rule(::Type{BigInt}, ::Type{Int8}) = BigInt
```

Dans ce dernier cas, le type de résultat est [`BigInt`](@ref) puisque `BigInt` est le seul type suffisamment grand pour contenir des entiers pour l'arithmétique des entiers à précision arbitraire. Notez également qu'il n'est pas nécessaire de définir à la fois `promote_rule(::Type{A}, ::Type{B})` et `promote_rule(::Type{B}, ::Type{A})` – la symétrie est implicite dans la façon dont `promote_rule` est utilisé dans le processus de promotion.

La fonction `promote_rule` est utilisée comme un élément de base pour définir une seconde fonction appelée [`promote_type`](@ref), qui, étant donné n'importe quel nombre d'objets de type, renvoie le type commun auquel ces valeurs, en tant qu'arguments de `promote`, devraient être promues. Ainsi, si l'on veut savoir, en l'absence de valeurs réelles, quel type une collection de valeurs de certains types serait promue, on peut utiliser `promote_type` :

```jldoctest
julia> promote_type(Int8, Int64)
Int64
```

Notez que nous ne surchargeons **pas** directement `promote_type` : nous surchargeons plutôt `promote_rule`. `promote_type` utilise `promote_rule` et ajoute la symétrie. Surcharger directement peut entraîner des erreurs d'ambiguïté. Nous surchargeons `promote_rule` pour définir comment les choses doivent être promues, et nous utilisons `promote_type` pour interroger cela.

En interne, `promote_type` est utilisé à l'intérieur de `promote` pour déterminer quel type de valeurs d'argument doivent être converties pour la promotion. Le lecteur curieux peut lire le code dans [`promotion.jl`](https://github.com/JuliaLang/julia/blob/master/base/promotion.jl), qui définit le mécanisme de promotion complet en environ 35 lignes.

### Case Study: Rational Promotions

Enfin, nous terminons notre étude de cas en cours sur le type de nombre rationnel de Julia, qui utilise de manière relativement sophistiquée le mécanisme de promotion avec les règles de promotion suivantes :

```julia
import Base: promote_rule
promote_rule(::Type{Rational{T}}, ::Type{S}) where {T<:Integer,S<:Integer} = Rational{promote_type(T,S)}
promote_rule(::Type{Rational{T}}, ::Type{Rational{S}}) where {T<:Integer,S<:Integer} = Rational{promote_type(T,S)}
promote_rule(::Type{Rational{T}}, ::Type{S}) where {T<:Integer,S<:AbstractFloat} = promote_type(T,S)
```

La première règle stipule que la promotion d'un nombre rationnel avec tout autre type entier se traduit par une promotion à un type rationnel dont le type du numérateur/dénominateur est le résultat de la promotion de son type de numérateur/dénominateur avec l'autre type entier. La deuxième règle applique la même logique à deux types différents de nombres rationnels, résultant en un rationnel de la promotion de leurs types respectifs de numérateur/dénominateur. La troisième et dernière règle dicte que la promotion d'un rationnel avec un flottant donne le même type que la promotion du type de numérateur/dénominateur avec le flottant.

Ce petit ensemble de règles de promotion, associé aux constructeurs de type et à la méthode `convert` par défaut pour les nombres, est suffisant pour permettre aux nombres rationnels d'interagir de manière complètement naturelle avec tous les autres types numériques de Julia – entiers, nombres à virgule flottante et nombres complexes. En fournissant des méthodes de conversion appropriées et des règles de promotion de la même manière, tout type numérique défini par l'utilisateur peut interagir tout aussi naturellement avec les numériques prédéfinis de Julia.
