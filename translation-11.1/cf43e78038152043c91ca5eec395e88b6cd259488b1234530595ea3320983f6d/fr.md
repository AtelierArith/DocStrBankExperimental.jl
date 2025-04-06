# [Performance Tips](@id man-performance-tips)

Dans les sections suivantes, nous passerons brièvement en revue quelques techniques qui peuvent aider à rendre votre code Julia aussi rapide que possible.

## Performance critical code should be inside a function

Tout code qui est critique pour la performance doit être à l'intérieur d'une fonction. Le code à l'intérieur des fonctions a tendance à s'exécuter beaucoup plus rapidement que le code de niveau supérieur, en raison du fonctionnement du compilateur de Julia.

L'utilisation de fonctions n'est pas seulement importante pour la performance : les fonctions sont plus réutilisables et testables, et clarifient quelles étapes sont effectuées et quels sont leurs entrées et sorties, [Write functions, not just scripts](@ref) est également une recommandation du Styleguide de Julia.

Les fonctions devraient prendre des arguments, au lieu d'opérer directement sur des variables globales, voir le point suivant.

## Avoid untyped global variables

La valeur d'une variable globale non typée peut changer à tout moment, ce qui peut entraîner un changement de son type. Cela rend difficile pour le compilateur d'optimiser le code utilisant des variables globales. Cela s'applique également aux variables de type, c'est-à-dire aux alias de type au niveau global. Les variables devraient être locales ou passées en tant qu'arguments aux fonctions, chaque fois que cela est possible.

Nous constatons que les noms globaux sont souvent des constantes, et les déclarer comme tels améliore considérablement les performances :

```julia
const DEFAULT_VAL = 0
```

Si un global est connu pour être toujours du même type, [the type should be annotated](@ref man-typed-globals).

L'utilisation de variables globales non typées peut être optimisée en annotant leurs types au point d'utilisation :

```julia
global x = rand(1000)

function loop_over_global()
    s = 0.0
    for i in x::Vector{Float64}
        s += i
    end
    return s
end
```

Passer des arguments aux fonctions est un meilleur style. Cela conduit à un code plus réutilisable et clarifie quels sont les entrées et les sorties.

!!! note
    Tout le code dans le REPL est évalué dans le scope global, donc une variable définie et assignée au niveau supérieur sera une variable **globale**. Les variables définies au niveau supérieur dans les modules sont également globales.


Dans la session REPL suivante :

```julia-repl
julia> x = 1.0
```

est équivalent à :

```julia-repl
julia> global x = 1.0
```

donc tous les problèmes de performance discutés précédemment s'appliquent.

## Measure performance with [`@time`](@ref) and pay attention to memory allocation

Un outil utile pour mesurer la performance est la macro [`@time`](@ref). Nous répétons ici l'exemple avec la variable globale ci-dessus, mais cette fois sans l'annotation de type :

```jldoctest; setup = :(using Random; Random.seed!(1234)), filter = r"[0-9\.]+ seconds \(.*?\)"
julia> x = rand(1000);

julia> function sum_global()
           s = 0.0
           for i in x
               s += i
           end
           return s
       end;

julia> @time sum_global()
  0.011539 seconds (9.08 k allocations: 373.386 KiB, 98.69% compilation time)
523.0007221951678

julia> @time sum_global()
  0.000091 seconds (3.49 k allocations: 70.156 KiB)
523.0007221951678
```

Lors du premier appel (`@time sum_global()`), la fonction est compilée. (Si vous n'avez pas encore utilisé [`@time`](@ref) dans cette session, elle compilera également les fonctions nécessaires pour le chronométrage.) Vous ne devez pas prendre les résultats de cette exécution au sérieux. Pour la deuxième exécution, notez qu'en plus de rapporter le temps, elle a également indiqué qu'une quantité significative de mémoire avait été allouée. Nous sommes ici simplement en train de calculer une somme sur tous les éléments d'un vecteur de flottants 64 bits, donc il ne devrait pas y avoir besoin d'allouer de la mémoire (sur le tas).

Nous devrions clarifier que ce que `@time` rapporte concerne spécifiquement les allocations de *tas*, qui sont généralement nécessaires pour des objets mutables ou pour créer/agrandir des conteneurs de taille variable (comme `Array` ou `Dict`, des chaînes de caractères, ou des objets "non stables" dont le type n'est connu qu'à l'exécution). L'allocation (ou la désallocation) de tels blocs de mémoire peut nécessiter un appel de fonction coûteux à libc (par exemple via `malloc` en C), et ils doivent être suivis pour la collecte des ordures. En revanche, les valeurs immuables comme les nombres (sauf les bignums), les tuples et les `struct`s immuables peuvent être stockées beaucoup plus facilement, par exemple dans la mémoire de la pile ou des registres CPU, donc on ne s'inquiète généralement pas du coût de performance de leur "allocation".

Une allocation de mémoire inattendue est presque toujours un signe de problème dans votre code, généralement un problème de stabilité de type ou la création de nombreux petits tableaux temporaires. Par conséquent, en plus de l'allocation elle-même, il est très probable que le code généré pour votre fonction soit loin d'être optimal. Prenez ces indications au sérieux et suivez les conseils ci-dessous.

Dans ce cas particulier, l'allocation de mémoire est due à l'utilisation d'une variable globale `x` de type instable, donc si nous passons `x` en tant qu'argument à la fonction, elle n'alloue plus de mémoire (l'allocation restante rapportée ci-dessous est due à l'exécution de la macro `@time` dans le scope global) et est significativement plus rapide après le premier appel :

```jldoctest sumarg; setup = :(using Random; Random.seed!(1234)), filter = r"[0-9\.]+ seconds \(.*?\)"
julia> x = rand(1000);

julia> function sum_arg(x)
           s = 0.0
           for i in x
               s += i
           end
           return s
       end;

julia> @time sum_arg(x)
  0.007551 seconds (3.98 k allocations: 200.548 KiB, 99.77% compilation time)
523.0007221951678

julia> @time sum_arg(x)
  0.000006 seconds (1 allocation: 16 bytes)
523.0007221951678
```

L'allocation de 1 vue est due à l'exécution de la macro `@time` elle-même dans le scope global. Si nous exécutons plutôt le chronométrage dans une fonction, nous pouvons voir qu'en effet, aucune allocation n'est effectuée :

```jldoctest sumarg; filter = r"[0-9\.]+ seconds"
julia> time_sum(x) = @time sum_arg(x);

julia> time_sum(x)
  0.000002 seconds
523.0007221951678
```

Dans certaines situations, votre fonction peut avoir besoin d'allouer de la mémoire dans le cadre de son fonctionnement, et cela peut compliquer l'image simple ci-dessus. Dans de tels cas, envisagez d'utiliser l'un des [tools](@ref tools) ci-dessous pour diagnostiquer des problèmes, ou écrivez une version de votre fonction qui sépare l'allocation de ses aspects algorithmiques (voir [Pre-allocating outputs](@ref)).

!!! note
    Pour des benchmarks plus sérieux, envisagez le package [BenchmarkTools.jl](https://github.com/JuliaCI/BenchmarkTools.jl) qui, entre autres choses, évalue la fonction plusieurs fois afin de réduire le bruit.


## [Tools](@id tools)

Julia et son écosystème de packages incluent des outils qui peuvent vous aider à diagnostiquer des problèmes et à améliorer les performances de votre code :

  * [Profiling](@ref) vous permet de mesurer la performance de votre code en cours d'exécution et d'identifier les lignes qui constituent des goulets d'étranglement. Pour des projets complexes, le package [ProfileView](https://github.com/timholy/ProfileView.jl) peut vous aider à visualiser vos résultats de profilage.
  * Le package [JET](https://github.com/aviatesk/JET.jl) peut vous aider à identifier les problèmes de performance courants dans votre code.
  * Des allocations de mémoire inattendues et importantes – comme le rapportent [`@time`](@ref), [`@allocated`](@ref), ou le profileur (via des appels aux routines de collecte des ordures) – suggèrent qu'il pourrait y avoir des problèmes avec votre code. Si vous ne voyez pas d'autre raison pour les allocations, soupçonnez un problème de type. Vous pouvez également démarrer Julia avec l'option `--track-allocation=user` et examiner les fichiers `*.mem` résultants pour voir des informations sur l'endroit où ces allocations se produisent. Voir [Memory allocation analysis](@ref).
  * `@code_warntype` génère une représentation de votre code qui peut être utile pour trouver des expressions qui entraînent une incertitude de type. Voir [`@code_warntype`](@ref) ci-dessous.

## [Avoid containers with abstract type parameters](@id man-performance-abstract-container)

Lorsqu'on travaille avec des types paramétrés, y compris les tableaux, il est préférable d'éviter de paramétrer avec des types abstraits lorsque cela est possible.

Veuillez considérer ce qui suit :

```jldoctest
julia> a = Real[]
Real[]

julia> push!(a, 1); push!(a, 2.0); push!(a, π)
3-element Vector{Real}:
 1
 2.0
 π = 3.1415926535897...
```

Parce que `a` est un tableau de type abstrait [`Real`](@ref), il doit être capable de contenir n'importe quelle valeur `Real`. Étant donné que les objets `Real` peuvent avoir une taille et une structure arbitraires, `a` doit être représenté comme un tableau de pointeurs vers des objets `Real` alloués individuellement. Cependant, si nous permettons plutôt uniquement de stocker des nombres du même type, par exemple [`Float64`](@ref), ceux-ci peuvent être stockés de manière plus efficace :

```jldoctest
julia> a = Float64[]
Float64[]

julia> push!(a, 1); push!(a, 2.0); push!(a,  π)
3-element Vector{Float64}:
 1.0
 2.0
 3.141592653589793
```

L'attribution de nombres à `a` les convertira désormais en `Float64` et `a` sera stocké comme un bloc contigu de valeurs flottantes de 64 bits qui peuvent être manipulées efficacement.

Si vous ne pouvez pas éviter les conteneurs avec des types de valeur abstraits, il est parfois préférable de paramétrer avec `Any` pour éviter la vérification de type à l'exécution. Par exemple, `IdDict{Any, Any}` fonctionne mieux que `IdDict{Type, Vector}`.

Voir aussi la discussion sous [Parametric Types](@ref).

## Type declarations

Dans de nombreuses langues avec des déclarations de type optionnelles, ajouter des déclarations est le principal moyen de rendre le code plus rapide. Ce n'est *pas* le cas en Julia. En Julia, le compilateur connaît généralement les types de tous les arguments de fonction, des variables locales et des expressions. Cependant, il existe quelques cas spécifiques où les déclarations sont utiles.

### Avoid fields with abstract type

Les types peuvent être déclarés sans spécifier les types de leurs champs :

```jldoctest myambig
julia> struct MyAmbiguousType
           a
       end
```

Cela permet à `a` d'être de n'importe quel type. Cela peut souvent être utile, mais cela a un inconvénient : pour les objets de type `MyAmbiguousType`, le compilateur ne pourra pas générer un code haute performance. La raison en est que le compilateur utilise les types des objets, et non leurs valeurs, pour déterminer comment construire le code. Malheureusement, très peu peut être déduit d'un objet de type `MyAmbiguousType` :

```jldoctest myambig
julia> b = MyAmbiguousType("Hello")
MyAmbiguousType("Hello")

julia> c = MyAmbiguousType(17)
MyAmbiguousType(17)

julia> typeof(b)
MyAmbiguousType

julia> typeof(c)
MyAmbiguousType
```

Les valeurs de `b` et `c` ont le même type, mais leur représentation sous-jacente des données en mémoire est très différente. Même si vous stockiez uniquement des valeurs numériques dans le champ `a`, le fait que la représentation en mémoire d'un [`UInt8`](@ref) diffère d'un [`Float64`](@ref) signifie également que le CPU doit les traiter en utilisant deux types d'instructions différents. Comme les informations requises ne sont pas disponibles dans le type, de telles décisions doivent être prises à l'exécution. Cela ralentit les performances.

Vous pouvez faire mieux en déclarant le type de `a`. Ici, nous nous concentrons sur le cas où `a` pourrait être l'un de plusieurs types, auquel cas la solution naturelle est d'utiliser des paramètres. Par exemple :

```jldoctest myambig2
julia> mutable struct MyType{T<:AbstractFloat}
           a::T
       end
```

C'est un meilleur choix que

```jldoctest myambig2
julia> mutable struct MyStillAmbiguousType
           a::AbstractFloat
       end
```

parce que la première version spécifie le type de `a` à partir du type de l'objet wrapper. Par exemple :

```jldoctest myambig2
julia> m = MyType(3.2)
MyType{Float64}(3.2)

julia> t = MyStillAmbiguousType(3.2)
MyStillAmbiguousType(3.2)

julia> typeof(m)
MyType{Float64}

julia> typeof(t)
MyStillAmbiguousType
```

Le type du champ `a` peut être facilement déterminé à partir du type de `m`, mais pas à partir du type de `t`. En effet, dans `t`, il est possible de changer le type du champ `a` :

```jldoctest myambig2
julia> typeof(t.a)
Float64

julia> t.a = 4.5f0
4.5f0

julia> typeof(t.a)
Float32
```

En revanche, une fois que `m` est construit, le type de `m.a` ne peut pas changer :

```jldoctest myambig2
julia> m.a = 4.5f0
4.5f0

julia> typeof(m.a)
Float64
```

Le fait que le type de `m.a` soit connu à partir du type de `m`—couplé avec le fait que son type ne peut pas changer en cours de fonction—permet au compilateur de générer un code hautement optimisé pour des objets comme `m` mais pas pour des objets comme `t`.

Bien sûr, tout cela est vrai uniquement si nous construisons `m` avec un type concret. Nous pouvons briser cela en le construisant explicitement avec un type abstrait :

```jldoctest myambig2
julia> m = MyType{AbstractFloat}(3.2)
MyType{AbstractFloat}(3.2)

julia> typeof(m.a)
Float64

julia> m.a = 4.5f0
4.5f0

julia> typeof(m.a)
Float32
```

Pour tous les usages pratiques, de tels objets se comportent de manière identique à ceux de `MyStillAmbiguousType`.

Il est assez instructif de comparer la quantité de code générée pour une fonction simple.

```julia
func(m::MyType) = m.a+1
```

utilisant

```julia
code_llvm(func, Tuple{MyType{Float64}})
code_llvm(func, Tuple{MyType{AbstractFloat}})
```

Pour des raisons de longueur, les résultats ne sont pas affichés ici, mais vous pouvez souhaiter essayer cela vous-même. Comme le type est entièrement spécifié dans le premier cas, le compilateur n'a pas besoin de générer de code pour résoudre le type à l'exécution. Cela se traduit par un code plus court et plus rapide.

Il faut également garder à l'esprit que les types non entièrement paramétrés se comportent comme des types abstraits. Par exemple, même si un `Array{T,n}` entièrement spécifié est concret, `Array` lui-même sans paramètres donnés n'est pas concret :

```jldoctest myambig3
julia> !isconcretetype(Array), !isabstracttype(Array), isstructtype(Array), !isconcretetype(Array{Int}), isconcretetype(Array{Int,1})
(true, true, true, true, true)
```

Dans ce cas, il vaudrait mieux éviter de déclarer `MyType` avec un champ `a::Array` et plutôt déclarer le champ comme `a::Array{T,N}` ou comme `a::A`, où `{T,N}` ou `A` sont des paramètres de `MyType`.

Le conseil précédent est particulièrement utile lorsque les champs d'une structure sont destinés à être des fonctions, ou plus généralement des objets appelables. Il est très tentant de définir une structure comme suit :

```julia
struct MyCallableWrapper
    f::Function
end
```

Mais comme `Function` est un type abstrait, chaque appel à `wrapper.f` nécessitera un dispatch dynamique, en raison de l'instabilité de type liée à l'accès au champ `f`. Au lieu de cela, vous devriez écrire quelque chose comme :

```julia
struct MyCallableWrapper{F}
    f::F
end
```

qui a un comportement presque identique mais sera beaucoup plus rapide (car l'instabilité de type est éliminée). Notez que nous n'imposons pas `F<:Function` : cela signifie que les objets appelables qui ne sous-typer `Function` sont également autorisés pour le champ `f`.

### Avoid fields with abstract containers

Les mêmes meilleures pratiques s'appliquent également aux types de conteneurs :

```jldoctest containers
julia> struct MySimpleContainer{A<:AbstractVector}
           a::A
       end

julia> struct MyAmbiguousContainer{T}
           a::AbstractVector{T}
       end

julia> struct MyAlsoAmbiguousContainer
           a::Array
       end
```

Pour exemple :

```jldoctest containers
julia> c = MySimpleContainer(1:3);

julia> typeof(c)
MySimpleContainer{UnitRange{Int64}}

julia> c = MySimpleContainer([1:3;]);

julia> typeof(c)
MySimpleContainer{Vector{Int64}}

julia> b = MyAmbiguousContainer(1:3);

julia> typeof(b)
MyAmbiguousContainer{Int64}

julia> b = MyAmbiguousContainer([1:3;]);

julia> typeof(b)
MyAmbiguousContainer{Int64}

julia> d = MyAlsoAmbiguousContainer(1:3);

julia> typeof(d), typeof(d.a)
(MyAlsoAmbiguousContainer, Vector{Int64})

julia> d = MyAlsoAmbiguousContainer(1:1.0:3);

julia> typeof(d), typeof(d.a)
(MyAlsoAmbiguousContainer, Vector{Float64})

```

Pour `MySimpleContainer`, l'objet est entièrement spécifié par son type et ses paramètres, de sorte que le compilateur peut générer des fonctions optimisées. Dans la plupart des cas, cela suffira probablement.

Bien que le compilateur puisse maintenant faire son travail parfaitement, il existe des cas où *vous* pourriez souhaiter que votre code puisse faire des choses différentes en fonction du *type d'élément* de `a`. En général, la meilleure façon d'y parvenir est d'encapsuler votre opération spécifique (ici, `foo`) dans une fonction séparée :

```jldoctest containers
julia> function sumfoo(c::MySimpleContainer)
           s = 0
           for x in c.a
               s += foo(x)
           end
           s
       end
sumfoo (generic function with 1 method)

julia> foo(x::Integer) = x
foo (generic function with 1 method)

julia> foo(x::AbstractFloat) = round(x)
foo (generic function with 2 methods)
```

Cela garde les choses simples, tout en permettant au compilateur de générer du code optimisé dans tous les cas.

Cependant, il existe des cas où vous devrez peut-être déclarer différentes versions de la fonction externe pour différents types d'éléments ou types de l'`AbstractVector` du champ `a` dans `MySimpleContainer`. Vous pourriez le faire comme ceci :

```jldoctest containers
julia> function myfunc(c::MySimpleContainer{<:AbstractArray{<:Integer}})
           return c.a[1]+1
       end
myfunc (generic function with 1 method)

julia> function myfunc(c::MySimpleContainer{<:AbstractArray{<:AbstractFloat}})
           return c.a[1]+2
       end
myfunc (generic function with 2 methods)

julia> function myfunc(c::MySimpleContainer{Vector{T}}) where T <: Integer
           return c.a[1]+3
       end
myfunc (generic function with 3 methods)
```

```jldoctest containers
julia> myfunc(MySimpleContainer(1:3))
2

julia> myfunc(MySimpleContainer(1.0:3))
3.0

julia> myfunc(MySimpleContainer([1:3;]))
4
```

### Annotate values taken from untyped locations

Il est souvent pratique de travailler avec des structures de données qui peuvent contenir des valeurs de n'importe quel type (tableaux de type `Array{Any}`). Mais, si vous utilisez l'une de ces structures et que vous savez quel est le type d'un élément, il est utile de partager cette connaissance avec le compilateur :

```julia
function foo(a::Array{Any,1})
    x = a[1]::Int32
    b = x+1
    ...
end
```

Ici, nous avons eu la chance de savoir que le premier élément de `a` serait un [`Int32`](@ref). Faire une annotation comme celle-ci a l'avantage supplémentaire de provoquer une erreur d'exécution si la valeur n'est pas du type attendu, ce qui peut potentiellement attraper certains bugs plus tôt.

Dans le cas où le type de `a[1]` n'est pas connu précisément, `x` peut être déclaré via `x = convert(Int32, a[1])::Int32`. L'utilisation de la fonction [`convert`](@ref) permet à `a[1]` d'être n'importe quel objet convertible en `Int32` (tel que `UInt8`), augmentant ainsi la généricité du code en assouplissant l'exigence de type. Remarquez que `convert` lui-même a besoin d'une annotation de type dans ce contexte afin d'atteindre la stabilité de type. Cela est dû au fait que le compilateur ne peut pas déduire le type de la valeur de retour d'une fonction, même `convert`, à moins que les types de tous les arguments de la fonction soient connus.

L'annotation de type n'améliorera pas (et peut en fait nuire) aux performances si le type est abstrait ou construit à l'exécution. Cela est dû au fait que le compilateur ne peut pas utiliser l'annotation pour spécialiser le code suivant, et la vérification de type elle-même prend du temps. Par exemple, dans le code :

```julia
function nr(a, prec)
    ctype = prec == 32 ? Float32 : Float64
    b = Complex{ctype}(a)
    c = (b + 1.0f0)::Complex{ctype}
    abs(c)
end
```

l'annotation de `c` nuit à la performance. Pour écrire un code performant impliquant des types construits à l'exécution, utilisez le [function-barrier technique](@ref kernel-functions) discuté ci-dessous, et assurez-vous que le type construit figure parmi les types d'arguments de la fonction noyau afin que les opérations du noyau soient correctement spécialisées par le compilateur. Par exemple, dans l'extrait ci-dessus, dès que `b` est construit, il peut être passé à une autre fonction `k`, le noyau. Si, par exemple, la fonction `k` déclare `b` comme un argument de type `Complex{T}`, où `T` est un paramètre de type, alors une annotation de type apparaissant dans une instruction d'assignation au sein de `k` sous la forme :

```julia
c = (b + 1.0f0)::Complex{T}
```

n'entrave pas la performance (mais n'aide pas non plus) puisque le compilateur peut déterminer le type de `c` au moment où `k` est compilé.

### Be aware of when Julia avoids specializing

En tant qu'heuristique, Julia évite d'automatiquement [specializing](@ref man-method-specializations) sur les paramètres de type d'argument dans trois cas spécifiques : `Type`, `Function` et `Vararg`. Julia se spécialise toujours lorsque l'argument est utilisé dans la méthode, mais pas si l'argument est simplement transmis à une autre fonction. Cela n'a généralement aucun impact sur les performances à l'exécution et [improves compiler performance](@ref compiler-efficiency-issues). Si vous constatez que cela a un impact sur les performances à l'exécution dans votre cas, vous pouvez déclencher la spécialisation en ajoutant un paramètre de type à la déclaration de la méthode. Voici quelques exemples :

Cela ne se spécialisera pas :

```julia
function f_type(t)  # or t::Type
    x = ones(t, 10)
    return sum(map(sin, x))
end
```

mais cela le fera :

```julia
function g_type(t::Type{T}) where T
    x = ones(T, 10)
    return sum(map(sin, x))
end
```

Ces derniers ne se spécialiseront pas :

```julia
f_func(f, num) = ntuple(f, div(num, 2))
g_func(g::Function, num) = ntuple(g, div(num, 2))
```

mais cela le fera :

```julia
h_func(h::H, num) where {H} = ntuple(h, div(num, 2))
```

Cela ne se spécialisera pas :

```julia
f_vararg(x::Int...) = tuple(x...)
```

mais cela le fera :

```julia
g_vararg(x::Vararg{Int, N}) where {N} = tuple(x...)
```

Il suffit d'introduire un seul paramètre de type pour forcer la spécialisation, même si les autres types ne sont pas contraints. Par exemple, cela se spécialise également et est utile lorsque les arguments ne sont pas tous du même type :

```julia
h_vararg(x::Vararg{Any, N}) where {N} = tuple(x...)
```

Notez que [`@code_typed`](@ref) et ses amis vous montreront toujours du code spécialisé, même si Julia ne spécialiserait normalement pas cet appel de méthode. Vous devez vérifier le [method internals](@ref ast-lowered-method) si vous voulez voir si des spécialisations sont générées lorsque les types d'arguments sont modifiés, c'est-à-dire si `Base.specializations(@which f(...))` contient des spécialisations pour l'argument en question.

## Break functions into multiple definitions

Écrire une fonction sous forme de nombreuses petites définitions permet au compilateur d'appeler directement le code le plus applicable, voire de l'inclure en ligne.

Voici un exemple de "fonction composée" qui devrait vraiment être écrite comme plusieurs définitions :

```julia
using LinearAlgebra

function mynorm(A)
    if isa(A, Vector)
        return sqrt(real(dot(A,A)))
    elseif isa(A, Matrix)
        return maximum(svdvals(A))
    else
        error("mynorm: invalid argument")
    end
end
```

Cela peut être écrit de manière plus concise et efficace comme suit :

```julia
mynorm(x::Vector) = sqrt(real(dot(x, x)))
mynorm(A::Matrix) = maximum(svdvals(A))
```

Il convient cependant de noter que le compilateur est assez efficace pour optimiser les branches mortes dans le code écrit comme l'exemple `mynorm`.

## Write "type-stable" functions

Lorsqu'il est possible, il est utile de s'assurer qu'une fonction renvoie toujours une valeur du même type. Considérez la définition suivante :

```julia
pos(x) = x < 0 ? 0 : x
```

Bien que cela semble assez innocent, le problème est que `0` est un entier (de type `Int`) et que `x` peut être de n'importe quel type. Ainsi, en fonction de la valeur de `x`, cette fonction peut renvoyer une valeur de l'un ou l'autre de deux types. Ce comportement est autorisé et peut être souhaitable dans certains cas. Mais cela peut facilement être corrigé comme suit :

```julia
pos(x) = x < 0 ? zero(x) : x
```

Il y a aussi une fonction [`oneunit`](@ref), et une fonction plus générale [`oftype(x, y)`](@ref), qui retourne `y` converti au type de `x`.

## Avoid changing the type of a variable

Un problème analogue de "stabilité de type" existe pour les variables utilisées plusieurs fois dans une fonction :

```julia
function foo()
    x = 1
    for i = 1:10
        x /= rand()
    end
    return x
end
```

La variable locale `x` commence comme un entier, et après une itération de boucle devient un nombre à virgule flottante (le résultat de l'opérateur [`/`](@ref)). Cela rend plus difficile pour le compilateur d'optimiser le corps de la boucle. Il existe plusieurs solutions possibles :

  * Initialiser `x` avec `x = 1.0`
  * Déclarez le type de `x` explicitement comme `x::Float64 = 1`
  * Utilisez une conversion explicite par `x = oneunit(Float64)`
  * Initialisez avec la première itération de boucle, à `x = 1 / rand()`, puis boucle `for i = 2:10`

## [Separate kernel functions (aka, function barriers)](@id kernel-functions)

De nombreuses fonctions suivent un schéma consistant à effectuer un certain travail de préparation, puis à exécuter de nombreuses itérations pour réaliser un calcul central. Lorsque cela est possible, il est judicieux de placer ces calculs centraux dans des fonctions séparées. Par exemple, la fonction fictive suivante renvoie un tableau d'un type choisi au hasard :

```jldoctest; setup = :(using Random; Random.seed!(1234))
julia> function strange_twos(n)
           a = Vector{rand(Bool) ? Int64 : Float64}(undef, n)
           for i = 1:n
               a[i] = 2
           end
           return a
       end;

julia> strange_twos(3)
3-element Vector{Int64}:
 2
 2
 2
```

Cela devrait être écrit comme :

```jldoctest; setup = :(using Random; Random.seed!(1234))
julia> function fill_twos!(a)
           for i = eachindex(a)
               a[i] = 2
           end
       end;

julia> function strange_twos(n)
           a = Vector{rand(Bool) ? Int64 : Float64}(undef, n)
           fill_twos!(a)
           return a
       end;

julia> strange_twos(3)
3-element Vector{Int64}:
 2
 2
 2
```

Le compilateur de Julia spécialise le code pour les types d'arguments aux frontières des fonctions, donc dans l'implémentation originale, il ne connaît pas le type de `a` pendant la boucle (puisqu'il est choisi aléatoirement). Par conséquent, la deuxième version est généralement plus rapide puisque la boucle interne peut être recompilée dans le cadre de `fill_twos!` pour différents types de `a`.

La deuxième forme est également souvent un meilleur style et peut conduire à une plus grande réutilisation du code.

Ce modèle est utilisé à plusieurs endroits dans Julia Base. Par exemple, voir `vcat` et `hcat` dans [`abstractarray.jl`](https://github.com/JuliaLang/julia/blob/40fe264f4ffaa29b749bcf42239a89abdcbba846/base/abstractarray.jl#L1205-L1206), ou la fonction [`fill!`](@ref), que nous aurions pu utiliser au lieu d'écrire notre propre `fill_twos!`.

Des fonctions comme `strange_twos` se produisent lors de la manipulation de données de type incertain, par exemple des données chargées à partir d'un fichier d'entrée qui pourrait contenir soit des entiers, des flottants, des chaînes de caractères ou autre chose.

## [Types with values-as-parameters](@id man-performance-value-type)

Disons que vous souhaitez créer un tableau `N`-dimensionnel qui a une taille de 3 le long de chaque axe. De tels tableaux peuvent être créés comme ceci :

```jldoctest
julia> A = fill(5.0, (3, 3))
3×3 Matrix{Float64}:
 5.0  5.0  5.0
 5.0  5.0  5.0
 5.0  5.0  5.0
```

Cette approche fonctionne très bien : le compilateur peut déterminer que `A` est un `Array{Float64,2}` car il connaît le type de la valeur de remplissage (`5.0::Float64`) et la dimensionnalité (`(3, 3)::NTuple{2,Int}`). Cela implique que le compilateur peut générer un code très efficace pour toute utilisation future de `A` dans la même fonction.

Mais maintenant, disons que vous voulez écrire une fonction qui crée un tableau 3×3×... dans des dimensions arbitraires ; vous pourriez être tenté d'écrire une fonction

```jldoctest
julia> function array3(fillval, N)
           fill(fillval, ntuple(d->3, N))
       end
array3 (generic function with 1 method)

julia> array3(5.0, 2)
3×3 Matrix{Float64}:
 5.0  5.0  5.0
 5.0  5.0  5.0
 5.0  5.0  5.0
```

Cela fonctionne, mais (comme vous pouvez le vérifier vous-même en utilisant `@code_warntype array3(5.0, 2)`) le problème est que le type de sortie ne peut pas être inféré : l'argument `N` est une *valeur* de type `Int`, et l'inférence de type ne peut pas (et ne peut pas) prédire sa valeur à l'avance. Cela signifie que le code utilisant la sortie de cette fonction doit être conservateur, vérifiant le type à chaque accès de `A` ; ce type de code sera très lent.

Maintenant, une très bonne façon de résoudre de tels problèmes est d'utiliser le [function-barrier technique](@ref kernel-functions). Cependant, dans certains cas, vous pourriez vouloir éliminer complètement l'instabilité de type. Dans de tels cas, une approche consiste à passer la dimensionnalité en tant que paramètre, par exemple via `Val{T}()` (voir ["Value types"](@ref)):

```jldoctest
julia> function array3(fillval, ::Val{N}) where N
           fill(fillval, ntuple(d->3, Val(N)))
       end
array3 (generic function with 1 method)

julia> array3(5.0, Val(2))
3×3 Matrix{Float64}:
 5.0  5.0  5.0
 5.0  5.0  5.0
 5.0  5.0  5.0
```

Julia a une version spécialisée de `ntuple` qui accepte une instance `Val{::Int}` comme deuxième paramètre ; en passant `N` comme paramètre de type, vous rendez sa "valeur" connue au compilateur. Par conséquent, cette version de `array3` permet au compilateur de prédire le type de retour.

Cependant, l'utilisation de telles techniques peut être étonnamment subtile. Par exemple, cela ne servirait à rien si vous appeliez `array3` depuis une fonction comme celle-ci :

```julia
function call_array3(fillval, n)
    A = array3(fillval, Val(n))
end
```

Ici, vous avez recréé le même problème encore une fois : le compilateur ne peut pas deviner ce que `n` est, donc il ne connaît pas le *type* de `Val(n)`. Tenter d'utiliser `Val`, mais le faire incorrectement, peut facilement rendre les performances *pire* dans de nombreuses situations. (Ce n'est que dans les situations où vous combinez effectivement `Val` avec le truc de barrière de fonction, pour rendre la fonction noyau plus efficace, que du code comme ci-dessus devrait être utilisé.)

Un exemple d'utilisation correcte de `Val` serait :

```julia
function filter3(A::AbstractArray{T,N}) where {T,N}
    kernel = array3(1, Val(N))
    filter(A, kernel)
end
```

Dans cet exemple, `N` est passé en tant que paramètre, donc sa "valeur" est connue du compilateur. Essentiellement, `Val(T)` fonctionne uniquement lorsque `T` est soit codé en dur/littéral (`Val(3)`), soit déjà spécifié dans le domaine des types.

## The dangers of abusing multiple dispatch (aka, more on types with values-as-parameters)

Une fois qu'on apprend à apprécier le dispatch multiple, il y a une tendance compréhensible à en abuser et à essayer de l'utiliser pour tout. Par exemple, vous pourriez imaginer l'utiliser pour stocker des informations, c'est-à-dire

```
struct Car{Make, Model}
    year::Int
    ...more fields...
end
```

et ensuite dispatcher sur des objets comme `Car{:Honda,:Accord}(année, args...)`.

Cela pourrait être utile lorsque l'une des conditions suivantes est vraie :

  * Vous avez besoin d'un traitement intensif en CPU sur chaque `Car`, et cela devient beaucoup plus efficace si vous connaissez la `Make` et le `Model` au moment de la compilation et que le nombre total de `Make` ou `Model` différents qui seront utilisés n'est pas trop élevé.
  * Vous avez des listes homogènes du même type de `Car` à traiter, afin de pouvoir les stocker toutes dans un `Array{Car{:Honda,:Accord},N}`.

Lorsque ce dernier cas s'applique, une fonction traitant un tel tableau homogène peut être spécialisée de manière productive : Julia connaît le type de chaque élément à l'avance (tous les objets dans le conteneur ont le même type concret), donc Julia peut "rechercher" les appels de méthode corrects lorsque la fonction est compilée (évitant ainsi la nécessité de vérifier à l'exécution) et émettre ainsi un code efficace pour traiter l'ensemble de la liste.

Lorsque ces conditions ne sont pas remplies, il est probable que vous n'obteniez aucun avantage ; pire encore, l'"explosion combinatoire des types" qui en résulte sera contre-productive. Si `items[i+1]` a un type différent de `item[i]`, Julia doit rechercher le type à l'exécution, chercher la méthode appropriée dans les tables de méthodes, décider (via l'intersection des types) laquelle correspond, déterminer si elle a déjà été compilée JIT (et le faire si ce n'est pas le cas), puis effectuer l'appel. En essence, vous demandez à l'ensemble du système de types et à la machinerie de compilation JIT d'exécuter essentiellement l'équivalent d'une instruction switch ou d'une recherche dans un dictionnaire dans votre propre code.

Certaines références de performances à l'exécution comparant (1) le dispatch de type, (2) la recherche dans un dictionnaire, et (3) une instruction "switch" peuvent être trouvées [on the mailing list](https://groups.google.com/forum/#!msg/julia-users/jUMu9A3QKQQ/qjgVWr7vAwAJ).

Peut-être même pire que l'impact à l'exécution est l'impact à la compilation : Julia compilera des fonctions spécialisées pour chaque type différent `Car{Make, Model}` ; si vous avez des centaines ou des milliers de ces types, alors chaque fonction qui accepte un tel objet comme paramètre (d'une fonction `get_year` personnalisée que vous pourriez écrire vous-même, à la fonction générique `push!` dans Julia Base) aura des centaines ou des milliers de variantes compilées. Chacune de ces variantes augmente la taille du cache de code compilé, la longueur des listes internes de méthodes, etc. Un enthousiasme excessif pour les valeurs en tant que paramètres peut facilement gaspiller d'énormes ressources.

## [Access arrays in memory order, along columns](@id man-performance-column-major)

Les tableaux multidimensionnels en Julia sont stockés en ordre de colonne. Cela signifie que les tableaux sont empilés une colonne à la fois. Cela peut être vérifié en utilisant la fonction `vec` ou la syntaxe `[:]` comme montré ci-dessous (remarquez que le tableau est ordonné `[1 3 2 4]`, et non `[1 2 3 4]`) :

```jldoctest
julia> x = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> x[:]
4-element Vector{Int64}:
 1
 3
 2
 4
```

Cette convention pour l'ordre des tableaux est courante dans de nombreux langages comme Fortran, Matlab et R (pour n'en nommer que quelques-uns). L'alternative à l'ordre par colonne est l'ordre par ligne, qui est la convention adoptée par C et Python (`numpy`) parmi d'autres langages. Se souvenir de l'ordre des tableaux peut avoir des effets significatifs sur les performances lors de la boucle sur les tableaux. Une règle de base à garder à l'esprit est qu'avec des tableaux en ordre par colonne, le premier index change le plus rapidement. Essentiellement, cela signifie que la boucle sera plus rapide si l'index de la boucle la plus interne est le premier à apparaître dans une expression de tranche. Gardez à l'esprit que l'indexation d'un tableau avec `:` est une boucle implicite qui accède de manière itérative à tous les éléments dans une dimension particulière ; il peut être plus rapide d'extraire des colonnes que des lignes, par exemple.

Considérez l'exemple suivant. Imaginez que nous voulions écrire une fonction qui accepte un [`Vector`](@ref) et retourne un carré [`Matrix`](@ref) avec soit les lignes soit les colonnes remplies de copies du vecteur d'entrée. Supposons qu'il n'est pas important que ce soient les lignes ou les colonnes qui soient remplies avec ces copies (peut-être que le reste du code peut être facilement adapté en conséquence). Nous pourrions concevablement faire cela de quatre manières au moins (en plus de l'appel recommandé à la fonction intégrée [`repeat`](@ref)) :

```julia
function copy_cols(x::Vector{T}) where T
    inds = axes(x, 1)
    out = similar(Array{T}, inds, inds)
    for i = inds
        out[:, i] = x
    end
    return out
end

function copy_rows(x::Vector{T}) where T
    inds = axes(x, 1)
    out = similar(Array{T}, inds, inds)
    for i = inds
        out[i, :] = x
    end
    return out
end

function copy_col_row(x::Vector{T}) where T
    inds = axes(x, 1)
    out = similar(Array{T}, inds, inds)
    for col = inds, row = inds
        out[row, col] = x[row]
    end
    return out
end

function copy_row_col(x::Vector{T}) where T
    inds = axes(x, 1)
    out = similar(Array{T}, inds, inds)
    for row = inds, col = inds
        out[row, col] = x[col]
    end
    return out
end
```

Maintenant, nous allons chronométrer chacune de ces fonctions en utilisant le même vecteur d'entrée aléatoire `10000` par `1` :

```julia-repl
julia> x = randn(10000);

julia> fmt(f) = println(rpad(string(f)*": ", 14, ' '), @elapsed f(x))

julia> map(fmt, [copy_cols, copy_rows, copy_col_row, copy_row_col]);
copy_cols:    0.331706323
copy_rows:    1.799009911
copy_col_row: 0.415630047
copy_row_col: 1.721531501
```

Remarquez que `copy_cols` est beaucoup plus rapide que `copy_rows`. Cela est attendu car `copy_cols` respecte la disposition mémoire basée sur les colonnes de la `Matrix` et la remplit une colonne à la fois. De plus, `copy_col_row` est beaucoup plus rapide que `copy_row_col` car il suit notre règle empirique selon laquelle le premier élément à apparaître dans une expression de tranche doit être associé à la boucle la plus interne.

## Pre-allocating outputs

Si votre fonction renvoie un `Array` ou un autre type complexe, elle peut devoir allouer de la mémoire. Malheureusement, souvent, l'allocation et son inverse, la collecte des ordures, constituent des goulets d'étranglement substantiels.

Parfois, vous pouvez contourner le besoin d'allouer de la mémoire à chaque appel de fonction en préallouant la sortie. Comme exemple trivial, comparez

```jldoctest prealloc
julia> function xinc(x)
           return [x, x+1, x+2]
       end;

julia> function loopinc()
           y = 0
           for i = 1:10^7
               ret = xinc(i)
               y += ret[2]
           end
           return y
       end;
```

avec

```jldoctest prealloc
julia> function xinc!(ret::AbstractVector{T}, x::T) where T
           ret[1] = x
           ret[2] = x+1
           ret[3] = x+2
           nothing
       end;

julia> function loopinc_prealloc()
           ret = Vector{Int}(undef, 3)
           y = 0
           for i = 1:10^7
               xinc!(ret, i)
               y += ret[2]
           end
           return y
       end;
```

Résultats de chronométrage :

```jldoctest prealloc; filter = r"[0-9\.]+ seconds \(.*?\)"
julia> @time loopinc()
  0.529894 seconds (40.00 M allocations: 1.490 GiB, 12.14% gc time)
50000015000000

julia> @time loopinc_prealloc()
  0.030850 seconds (6 allocations: 288 bytes)
50000015000000
```

La préallocation a d'autres avantages, par exemple en permettant à l'appelant de contrôler le type "de sortie" d'un algorithme. Dans l'exemple ci-dessus, nous aurions pu passer un `SubArray` plutôt qu'un [`Array`](@ref), si nous l'avions souhaité.

Pris à son extrême, la pré-allocation peut rendre votre code plus moche, donc des mesures de performance et un certain jugement peuvent être nécessaires. Cependant, pour les fonctions "vectorisées" (élément par élément), la syntaxe pratique `x .= f.(y)` peut être utilisée pour des opérations en place avec des boucles fusionnées et sans tableaux temporaires (voir le [dot syntax for vectorizing functions](@ref man-vectorized)).

## [Use `MutableArithmetics` for more control over allocation for mutable arithmetic types](@id man-perftips-mutablearithmetics)

Certains sous-types [`Number`](@ref), tels que [`BigInt`](@ref) ou [`BigFloat`](@ref), peuvent être implémentés en tant que types [`mutable struct`](@ref), ou ils peuvent avoir des composants mutables. Les interfaces arithmétiques dans Julia `Base` choisissent généralement la commodité plutôt que l'efficacité dans de tels cas, donc les utiliser de manière naïve peut entraîner des performances sous-optimales. Les abstractions du package [`MutableArithmetics`](https://juliahub.com/ui/Packages/General/MutableArithmetics), en revanche, rendent possible l'exploitation de la mutabilité de tels types pour écrire un code rapide qui alloue uniquement ce qui est nécessaire. `MutableArithmetics` permet également de copier explicitement les valeurs des types arithmétiques mutables lorsque cela est nécessaire. `MutableArithmetics` est un package utilisateur et n'est pas affilié au projet Julia.

## More dots: Fuse vectorized operations

Julia a un [dot syntax](@ref man-vectorized) spécial qui convertit toute fonction scalaire en un appel de fonction "vectorisé", et tout opérateur en un opérateur "vectorisé", avec la propriété spéciale que les "appels de points" imbriqués sont *fusionnés* : ils sont combinés au niveau de la syntaxe en une seule boucle, sans allouer de tableaux temporaires. Si vous utilisez `.=` et des opérateurs d'assignation similaires, le résultat peut également être stocké sur place dans un tableau pré-alloué (voir ci-dessus).

Dans un contexte d'algèbre linéaire, cela signifie que même si des opérations comme `vector + vector` et `vector * scalar` sont définies, il peut être avantageux d'utiliser plutôt `vector .+ vector` et `vector .* scalar` car les boucles résultantes peuvent être fusionnées avec les calculs environnants. Par exemple, considérons les deux fonctions :

```jldoctest dotfuse
julia> f(x) = 3x.^2 + 4x + 7x.^3;

julia> fdot(x) = @. 3x^2 + 4x + 7x^3; # equivalent to 3 .* x.^2 .+ 4 .* x .+ 7 .* x.^3
```

Les deux `f` et `fdot` calculent la même chose. Cependant, `fdot` (défini avec l'aide du macro [`@.`](@ref @__dot__)) est significativement plus rapide lorsqu'il est appliqué à un tableau :

```jldoctest dotfuse; filter = r"[0-9\.]+ seconds \(.*?\)"
julia> x = rand(10^6);

julia> @time f(x);
  0.019049 seconds (16 allocations: 45.777 MiB, 18.59% gc time)

julia> @time fdot(x);
  0.002790 seconds (6 allocations: 7.630 MiB)

julia> @time f.(x);
  0.002626 seconds (8 allocations: 7.630 MiB)
```

C'est-à-dire que `fdot(x)` est dix fois plus rapide et alloue 1/6 de la mémoire de `f(x)`, car chaque opération `*` et `+` dans `f(x)` alloue un nouveau tableau temporaire et s'exécute dans une boucle séparée. Dans cet exemple, `f.(x)` est aussi rapide que `fdot(x)`, mais dans de nombreux contextes, il est plus pratique de parsemer vos expressions de quelques points que de définir une fonction séparée pour chaque opération vectorisée.

## [Fewer dots: Unfuse certain intermediate broadcasts](@id man-performance-unfuse)

La fusion de boucles dot mentionnée ci-dessus permet d'exprimer des opérations très performantes de manière concise et idiomatique. Cependant, il est important de se rappeler que l'opération fusionnée sera calculée à chaque itération de la diffusion. Cela signifie que dans certaines situations, en particulier en présence de diffusions composées ou multidimensionnelles, une expression avec des appels dot peut calculer une fonction plus de fois que prévu. Par exemple, disons que nous voulons construire une matrice aléatoire dont les lignes ont une norme euclidienne égale à un. Nous pourrions écrire quelque chose comme ce qui suit :

```
julia> x = rand(1000, 1000);

julia> d = sum(abs2, x; dims=2);

julia> @time x ./= sqrt.(d);
  0.002049 seconds (4 allocations: 96 bytes)
```

Cela fonctionnera. Cependant, cette expression recalculera en réalité `sqrt(d[i])` pour *chaque* élément de la ligne `x[i, :]`, ce qui signifie que beaucoup plus de racines carrées sont calculées que nécessaire. Pour voir précisément sur quels indices la diffusion itérera, nous pouvons appeler `Broadcast.combine_axes` sur les arguments de l'expression fusionnée. Cela renverra un tuple de plages dont les entrées correspondent aux axes d'itération ; le produit des longueurs de ces plages sera le nombre total d'appels à l'opération fusionnée.

Il s'ensuit que lorsque certains composants de l'expression de diffusion sont constants le long d'un axe—comme le `sqrt` le long de la deuxième dimension dans l'exemple précédent—il existe un potentiel d'amélioration des performances en "défusionnant" ces composants, c'est-à-dire en allouant à l'avance le résultat de l'opération diffusée et en réutilisant la valeur mise en cache le long de son axe constant. Certaines approches potentielles consistent à utiliser des variables temporaires, à envelopper des composants d'une expression de produit scalaire dans `identity`, ou à utiliser une fonction intrinsèquement vectorisée équivalente (mais non fusionnée).

```
julia> @time let s = sqrt.(d); x ./= s end;
  0.000809 seconds (5 allocations: 8.031 KiB)

julia> @time x ./= identity(sqrt.(d));
  0.000608 seconds (5 allocations: 8.031 KiB)

julia> @time x ./= map(sqrt, d);
  0.000611 seconds (4 allocations: 8.016 KiB)
```

L'une de ces options offre environ un triplement de la vitesse au prix d'une allocation ; pour de grands objets diffusables, cette accélération peut être asymptotiquement très importante.

## [Consider using views for slices](@id man-performance-views)

En Julia, une expression de "tranche" de tableau comme `array[1:5, :]` crée une copie de ces données (sauf du côté gauche d'une affectation, où `array[1:5, :] = ...` assigne en place à cette portion de `array`). Si vous effectuez de nombreuses opérations sur la tranche, cela peut être bon pour les performances car il est plus efficace de travailler avec une petite copie contiguë qu'il ne le serait d'indexer dans le tableau original. D'un autre côté, si vous ne faites que quelques opérations simples sur la tranche, le coût des opérations d'allocation et de copie peut être substantiel.

Une alternative consiste à créer une "vue" du tableau, qui est un objet tableau (un `SubArray`) qui référence en fait les données du tableau original sur place, sans faire de copie. (Si vous écrivez dans une vue, cela modifie également les données du tableau original.) Cela peut être fait pour des tranches individuelles en appelant [`view`](@ref), ou plus simplement pour une expression entière ou un bloc de code en mettant [`@views`](@ref) devant cette expression. Par exemple :

```jldoctest; filter = r"[0-9\.]+ seconds \(.*?\)"
julia> fcopy(x) = sum(x[2:end-1]);

julia> @views fview(x) = sum(x[2:end-1]);

julia> x = rand(10^6);

julia> @time fcopy(x);
  0.003051 seconds (3 allocations: 7.629 MB)

julia> @time fview(x);
  0.001020 seconds (1 allocation: 16 bytes)
```

Remarquez à la fois l'accélération de 3× et la diminution de l'allocation mémoire de la version `fview` de la fonction.

## Copying data is not always bad

Les tableaux sont stockés de manière contiguë en mémoire, ce qui les rend propices à la vectorisation par le CPU et à un nombre réduit d'accès mémoire grâce à la mise en cache. Ce sont les mêmes raisons pour lesquelles il est recommandé d'accéder aux tableaux dans l'ordre des colonnes (voir ci-dessus). Les motifs d'accès irréguliers et les vues non contiguës peuvent considérablement ralentir les calculs sur les tableaux en raison d'un accès mémoire non séquentiel.

Copier des données accédées de manière irrégulière dans un tableau contigu avant un accès répété peut entraîner un gain de vitesse important, comme dans l'exemple ci-dessous. Ici, une matrice est accédée à des indices mélangés de manière aléatoire avant d'être multipliée. Copier dans des tableaux simples accélère la multiplication même avec le coût supplémentaire de la copie et de l'allocation.

```julia-repl
julia> using Random

julia> A = randn(3000, 3000);

julia> x = randn(2000);

julia> inds = shuffle(1:3000)[1:2000];

julia> function iterated_neural_network(A, x, depth)
           for _ in 1:depth
               x .= max.(0, A * x)
           end
           argmax(x)
       end

julia> @time iterated_neural_network(view(A, inds, inds), x, 10)
  0.324903 seconds (12 allocations: 157.562 KiB)
1569

julia> @time iterated_neural_network(A[inds, inds], x, 10)
  0.054576 seconds (13 allocations: 30.671 MiB, 13.33% gc time)
1569
```

À condition qu'il y ait suffisamment de mémoire, le coût de la copie de la vue dans un tableau est compensé par l'augmentation de vitesse résultant des multiplications matricielles répétées sur un tableau contigu.

## Consider StaticArrays.jl for small fixed-size vector/matrix operations

Si votre application implique de nombreux petits tableaux (`< 100` éléments) de tailles fixes (c'est-à-dire que la taille est connue avant l'exécution), vous voudrez peut-être envisager d'utiliser le [StaticArrays.jl package](https://github.com/JuliaArrays/StaticArrays.jl). Ce package vous permet de représenter de tels tableaux d'une manière qui évite les allocations de tas inutiles et permet au compilateur de spécialiser le code pour la *taille* du tableau, par exemple en déroulant complètement les opérations vectorielles (éliminant les boucles) et en stockant les éléments dans des registres CPU.

Par exemple, si vous effectuez des calculs avec des géométries 2D, vous pourriez avoir de nombreux calculs avec des vecteurs à 2 composants. En utilisant le type `SVector` de StaticArrays.jl, vous pouvez utiliser une notation vectorielle pratique et des opérations comme `norm(3v - w)` sur les vecteurs `v` et `w`, tout en permettant au compilateur de dérouler le code pour un calcul minimal équivalent à `@inbounds hypot(3v[1]-w[1], 3v[2]-w[2])`.

## Avoid string interpolation for I/O

Lors de l'écriture de données dans un fichier (ou un autre périphérique d'E/S), la formation de chaînes intermédiaires supplémentaires est une source de surcharge. Au lieu de :

```julia
println(file, "$a $b")
```

utiliser :

```julia
println(file, a, " ", b)
```

La première version du code forme une chaîne, puis l'écrit dans le fichier, tandis que la deuxième version écrit directement les valeurs dans le fichier. Notez également que dans certains cas, l'interpolation de chaînes peut être plus difficile à lire. Considérez :

```julia
println(file, "$(f(a))$(f(b))")
```

contre :

```julia
println(file, f(a), f(b))
```

## Optimize network I/O during parallel execution

Lors de l'exécution d'une fonction distante en parallèle :

```julia
using Distributed

responses = Vector{Any}(undef, nworkers())
@sync begin
    for (idx, pid) in enumerate(workers())
        @async responses[idx] = remotecall_fetch(foo, pid, args...)
    end
end
```

est plus rapide que :

```julia
using Distributed

refs = Vector{Any}(undef, nworkers())
for (idx, pid) in enumerate(workers())
    refs[idx] = @spawnat pid foo(args...)
end
responses = [fetch(r) for r in refs]
```

Le premier entraîne un seul aller-retour réseau vers chaque travailleur, tandis que le second entraîne deux appels réseau - d'abord par le [`@spawnat`](@ref) et le second en raison du [`fetch`](@ref) (ou même un [`wait`](@ref)). Le `4d61726b646f776e2e436f64652822222c202266657463682229_40726566`/`4d61726b646f776e2e436f64652822222c2022776169742229_40726566` est également exécuté de manière sérielle, ce qui entraîne une performance globale inférieure.

## Fix deprecation warnings

Une fonction obsolète effectue en interne une recherche afin d'imprimer un avertissement pertinent une seule fois. Cette recherche supplémentaire peut entraîner un ralentissement significatif, donc toutes les utilisations de fonctions obsolètes doivent être modifiées comme le suggèrent les avertissements.

## Tweaks

Ce sont quelques points mineurs qui pourraient aider dans des boucles internes serrées.

  * Évitez les tableaux inutiles. Par exemple, au lieu de [`sum([x,y,z])`](@ref), utilisez `x+y+z`.
  * Utilisez [`abs2(z)`](@ref) au lieu de [`abs(z)^2`](@ref) pour des `z` complexes. En général, essayez de réécrire le code pour utiliser [`abs2`](@ref) au lieu de [`abs`](@ref) pour des arguments complexes.
  * Utilisez [`div(x,y)`](@ref) pour la division tronquée d'entiers au lieu de [`trunc(x/y)`](@ref), [`fld(x,y)`](@ref) au lieu de [`floor(x/y)`](@ref), et [`cld(x,y)`](@ref) au lieu de [`ceil(x/y)`](@ref).

## [Performance Annotations](@id man-performance-annotations)

Parfois, vous pouvez activer une meilleure optimisation en promettant certaines propriétés du programme.

  * Utilisez [`@inbounds`](@ref) pour éliminer la vérification des limites de tableau dans les expressions. Soyez certain avant de faire cela. Si les indices sont jamais hors limites, vous pourriez subir des plantages ou une corruption silencieuse.
  * Utilisez [`@fastmath`](@ref) pour permettre des optimisations en virgule flottante qui sont correctes pour les nombres réels, mais qui entraînent des différences pour les nombres IEEE. Soyez prudent lors de cette opération, car cela peut modifier les résultats numériques. Cela correspond à l'option `-ffast-math` de clang.
  * Écrivez [`@simd`](@ref) devant les boucles `for` pour promettre que les itérations sont indépendantes et peuvent être réorganisées. Notez que dans de nombreux cas, Julia peut automatiquement vectoriser le code sans le macro `@simd` ; cela n'est bénéfique que dans les cas où une telle transformation serait autrement illégale, y compris des cas comme permettre la réassociativité des flottants et ignorer les accès mémoire dépendants (`@simd ivdep`). Encore une fois, soyez très prudent lorsque vous affirmez `@simd`, car annoter erronément une boucle avec des itérations dépendantes peut entraîner des résultats inattendus. En particulier, notez que `setindex!` sur certains sous-types `AbstractArray` est intrinsèquement dépendant de l'ordre d'itération. **Cette fonctionnalité est expérimentale** et pourrait changer ou disparaître dans les futures versions de Julia.

L'idiome commun d'utiliser 1:n pour indexer un AbstractArray n'est pas sûr si l'Array utilise un indexage non conventionnel, et peut provoquer un défaut de segmentation si la vérification des limites est désactivée. Utilisez `LinearIndices(x)` ou `eachindex(x)` à la place (voir aussi [Arrays with custom indices](@ref man-custom-indices)).

!!! note
    Alors que `@simd` doit être placé directement devant une boucle `for` la plus interne, `@inbounds` et `@fastmath` peuvent être appliqués soit à des expressions uniques, soit à toutes les expressions qui apparaissent dans des blocs de code imbriqués, par exemple, en utilisant `@inbounds begin` ou `@inbounds for ...`.


Voici un exemple avec les balises `@inbounds` et `@simd` (nous utilisons ici `@noinline` pour empêcher l'optimiseur d'essayer d'être trop astucieux et de contrecarrer notre évaluation) :

```julia
@noinline function inner(x, y)
    s = zero(eltype(x))
    for i=eachindex(x)
        @inbounds s += x[i]*y[i]
    end
    return s
end

@noinline function innersimd(x, y)
    s = zero(eltype(x))
    @simd for i = eachindex(x)
        @inbounds s += x[i] * y[i]
    end
    return s
end

function timeit(n, reps)
    x = rand(Float32, n)
    y = rand(Float32, n)
    s = zero(Float64)
    time = @elapsed for j in 1:reps
        s += inner(x, y)
    end
    println("GFlop/sec        = ", 2n*reps / time*1E-9)
    time = @elapsed for j in 1:reps
        s += innersimd(x, y)
    end
    println("GFlop/sec (SIMD) = ", 2n*reps / time*1E-9)
end

timeit(1000, 1000)
```

Sur un ordinateur avec un processeur Intel Core i5 à 2,4 GHz, cela produit :

```
GFlop/sec        = 1.9467069505224963
GFlop/sec (SIMD) = 17.578554163920018
```

(`GFlop/sec` mesure la performance, et des nombres plus grands sont meilleurs.)

Voici un exemple avec les trois types de balisage. Ce programme calcule d'abord la différence finie d'un tableau unidimensionnel, puis évalue la norme L2 du résultat :

```julia
function init!(u::Vector)
    n = length(u)
    dx = 1.0 / (n-1)
    @fastmath @inbounds @simd for i in 1:n #by asserting that `u` is a `Vector` we can assume it has 1-based indexing
        u[i] = sin(2pi*dx*i)
    end
end

function deriv!(u::Vector, du)
    n = length(u)
    dx = 1.0 / (n-1)
    @fastmath @inbounds du[1] = (u[2] - u[1]) / dx
    @fastmath @inbounds @simd for i in 2:n-1
        du[i] = (u[i+1] - u[i-1]) / (2*dx)
    end
    @fastmath @inbounds du[n] = (u[n] - u[n-1]) / dx
end

function mynorm(u::Vector)
    n = length(u)
    T = eltype(u)
    s = zero(T)
    @fastmath @inbounds @simd for i in 1:n
        s += u[i]^2
    end
    @fastmath @inbounds return sqrt(s)
end

function main()
    n = 2000
    u = Vector{Float64}(undef, n)
    init!(u)
    du = similar(u)

    deriv!(u, du)
    nu = mynorm(du)

    @time for i in 1:10^6
        deriv!(u, du)
        nu = mynorm(du)
    end

    println(nu)
end

main()
```

Sur un ordinateur avec un processeur Intel Core i7 à 2,7 GHz, cela produit :

```
$ julia wave.jl;
  1.207814709 seconds
4.443986180758249

$ julia --math-mode=ieee wave.jl;
  4.487083643 seconds
4.443986180758249
```

Ici, l'option `--math-mode=ieee` désactive la macro `@fastmath`, afin que nous puissions comparer les résultats.

Dans ce cas, l'accélération due à `@fastmath` est d'un facteur d'environ 3,7. C'est exceptionnellement grand – en général, l'accélération sera plus petite. (Dans cet exemple particulier, l'ensemble de travail du benchmark est suffisamment petit pour tenir dans le cache L1 du processeur, de sorte que la latence d'accès à la mémoire ne joue pas de rôle, et le temps de calcul est dominé par l'utilisation du CPU. Dans de nombreux programmes du monde réel, ce n'est pas le cas.) De plus, dans ce cas, cette optimisation ne change pas le résultat – en général, le résultat sera légèrement différent. Dans certains cas, en particulier pour les algorithmes numériquement instables, le résultat peut être très différent.

L'annotation `@fastmath` réorganise les expressions à virgule flottante, par exemple en changeant l'ordre d'évaluation ou en supposant que certains cas particuliers (inf, nan) ne peuvent pas se produire. Dans ce cas (et sur cet ordinateur particulier), la principale différence est que l'expression `1 / (2*dx)` dans la fonction `deriv` est extraite de la boucle (c'est-à-dire calculée en dehors de la boucle), comme si l'on avait écrit `idx = 1 / (2*dx)`. Dans la boucle, l'expression `... / (2*dx)` devient alors `... * idx`, ce qui est beaucoup plus rapide à évaluer. Bien sûr, à la fois l'optimisation réelle appliquée par le compilateur et l'accélération résultante dépendent beaucoup du matériel. Vous pouvez examiner le changement dans le code généré en utilisant la fonction [`code_native`](@ref) de Julia.

Notez que `@fastmath` suppose également que des `NaN` ne se produiront pas pendant le calcul, ce qui peut entraîner un comportement surprenant :

```julia-repl
julia> f(x) = isnan(x);

julia> f(NaN)
true

julia> f_fast(x) = @fastmath isnan(x);

julia> f_fast(NaN)
false
```

## Treat Subnormal Numbers as Zeros

Les nombres subnormaux, anciennement appelés [denormal numbers](https://en.wikipedia.org/wiki/Denormal_number), sont utiles dans de nombreux contextes, mais entraînent une pénalité de performance sur certains matériels. Un appel [`set_zero_subnormals(true)`](@ref) accorde la permission aux opérations en virgule flottante de traiter les entrées ou sorties subnormales comme des zéros, ce qui peut améliorer les performances sur certains matériels. Un appel [`set_zero_subnormals(false)`](@ref) impose un comportement strict IEEE pour les nombres subnormaux.

Voici un exemple où les subnormaux ont un impact notable sur les performances de certains matériels :

```julia
function timestep(b::Vector{T}, a::Vector{T}, Δt::T) where T
    @assert length(a)==length(b)
    n = length(b)
    b[1] = 1                            # Boundary condition
    for i=2:n-1
        b[i] = a[i] + (a[i-1] - T(2)*a[i] + a[i+1]) * Δt
    end
    b[n] = 0                            # Boundary condition
end

function heatflow(a::Vector{T}, nstep::Integer) where T
    b = similar(a)
    for t=1:div(nstep,2)                # Assume nstep is even
        timestep(b,a,T(0.1))
        timestep(a,b,T(0.1))
    end
end

heatflow(zeros(Float32,10),2)           # Force compilation
for trial=1:6
    a = zeros(Float32,1000)
    set_zero_subnormals(iseven(trial))  # Odd trials use strict IEEE arithmetic
    @time heatflow(a,1000)
end
```

Cela donne une sortie similaire à

```
  0.002202 seconds (1 allocation: 4.063 KiB)
  0.001502 seconds (1 allocation: 4.063 KiB)
  0.002139 seconds (1 allocation: 4.063 KiB)
  0.001454 seconds (1 allocation: 4.063 KiB)
  0.002115 seconds (1 allocation: 4.063 KiB)
  0.001455 seconds (1 allocation: 4.063 KiB)
```

Notez comment chaque itération paire est significativement plus rapide.

Cet exemple génère de nombreux nombres subnormaux car les valeurs dans `a` deviennent une courbe exponentiellement décroissante, qui s'aplatit lentement au fil du temps.

Traiter les subnormaux comme des zéros doit être fait avec prudence, car cela casse certaines identités, telles que `x-y == 0` implique `x == y` :

```jldoctest
julia> x = 3f-38; y = 2f-38;

julia> set_zero_subnormals(true); (x - y, x == y)
(0.0f0, false)

julia> set_zero_subnormals(false); (x - y, x == y)
(1.0000001f-38, false)
```

Dans certaines applications, une alternative à la mise à zéro des nombres subnormaux consiste à injecter une petite quantité de bruit. Par exemple, au lieu d'initialiser `a` avec des zéros, initialisez-le avec :

```julia
a = rand(Float32,1000) * 1.f-9
```

## [[`@code_warntype`](@ref)](@id man-code-warntype)

Le macro [`@code_warntype`](@ref) (ou sa variante fonctionnelle [`code_warntype`](@ref)) peut parfois être utile pour diagnostiquer des problèmes liés aux types. Voici un exemple :

```julia-repl
julia> @noinline pos(x) = x < 0 ? 0 : x;

julia> function f(x)
           y = pos(x)
           return sin(y*x + 1)
       end;

julia> @code_warntype f(3.2)
MethodInstance for f(::Float64)
  from f(x) @ Main REPL[9]:1
Arguments
  #self#::Core.Const(f)
  x::Float64
Locals
  y::Union{Float64, Int64}
Body::Float64
1 ─      (y = Main.pos(x))
│   %2 = (y * x)::Float64
│   %3 = (%2 + 1)::Float64
│   %4 = Main.sin(%3)::Float64
└──      return %4
```

Interpréter la sortie de [`@code_warntype`](@ref), comme celle de ses cousines [`@code_lowered`](@ref), [`@code_typed`](@ref), [`@code_llvm`](@ref), et [`@code_native`](@ref), demande un peu de pratique. Votre code est présenté sous une forme qui a été fortement digérée en cours de génération de code machine compilé. La plupart des expressions sont annotées par un type, indiqué par le `::T` (où `T` pourrait être [`Float64`](@ref), par exemple). La caractéristique la plus importante de `4d61726b646f776e2e436f64652822222c202240636f64655f7761726e747970652229_40726566` est que les types non concrets sont affichés en ROUGE ; puisque ce document est écrit en Markdown, qui n'a pas de couleur, dans ce document, le texte rouge est désigné par des MAJUSCULES.

En haut, le type de retour inféré de la fonction est affiché comme `Body::Float64`. Les lignes suivantes représentent le corps de `f` sous la forme IR SSA de Julia. Les cases numérotées sont des étiquettes et représentent des cibles pour des sauts (via `goto`) dans votre code. En regardant le corps, vous pouvez voir que la première chose qui se passe est que `pos` est appelé et que la valeur de retour a été inférée comme étant le type `Union` `Union{Float64, Int64}` affiché en majuscules car il s'agit d'un type non concret. Cela signifie que nous ne pouvons pas connaître le type de retour exact de `pos` en fonction des types d'entrée. Cependant, le résultat de `y*x` est un `Float64` peu importe si `y` est un `Float64` ou un `Int64`. Le résultat net est que `f(x::Float64)` ne sera pas instable en termes de type dans sa sortie, même si certaines des calculs intermédiaires sont instables en termes de type.

Comment vous utilisez ces informations dépend de vous. Évidemment, il serait de loin préférable de fixer `pos` pour qu'il soit de type stable : si vous le faisiez, toutes les variables dans `f` seraient concrètes, et ses performances seraient optimales. Cependant, il existe des circonstances où ce type d'instabilité de type *éphémère* pourrait ne pas trop importer : par exemple, si `pos` n'est jamais utilisé isolément, le fait que la sortie de `f` soit de type stable (pour les entrées [`Float64`](@ref)) protégera le code ultérieur des effets propagés de l'instabilité de type. Cela est particulièrement pertinent dans les cas où il est difficile ou impossible de corriger l'instabilité de type. Dans de tels cas, les conseils ci-dessus (par exemple, ajouter des annotations de type et/ou décomposer les fonctions) sont vos meilleurs outils pour contenir les "dommages" causés par l'instabilité de type. De plus, notez que même Julia Base a des fonctions qui sont instables en termes de type. Par exemple, la fonction [`findfirst`](@ref) renvoie l'index dans un tableau où une clé est trouvée, ou `nothing` si elle n'est pas trouvée, une claire instabilité de type. Afin de faciliter la recherche des instabilités de type qui sont susceptibles d'être importantes, les `Union` contenant soit `missing` soit `nothing` sont mises en surbrillance en jaune, au lieu de rouge.

Les exemples suivants peuvent vous aider à interpréter les expressions marquées comme contenant des types non-feuilles :

  * Corps de fonction commençant par `Body::Union{T1,T2})`

      * Interprétation : fonction avec type de retour instable
      * Suggestion : rendre le type de valeur de retour stable, même si vous devez l'annoter.
  * `invoke Main.g(%%x::Int64)::Union{Float64, Int64}`

      * Interprétation : appel à une fonction `g` de type instable.
      * Suggestion : corrigez la fonction, ou si nécessaire, annotez la valeur de retour.
  * `invoke Base.getindex(%%x::Array{Any,1}, 1::Int64)::Any`

      * Interprétation : accès aux éléments de tableaux mal typés
      * Suggestion : utilisez des tableaux avec des types mieux définis, ou si nécessaire, annotez le type des accès aux éléments individuels.
  * `Base.getfield(%%x, :(:data))::Array{Float64,N} where N`

      * Interprétation : obtenir un champ qui n'est pas de type feuille. Dans ce cas, le type de `x`, disons `ArrayContainer`, avait un champ `data::Array{T}`. Mais `Array` a également besoin de la dimension `N` pour être un type concret.
      * Suggestion : utilisez des types concrets comme `Array{T,3}` ou `Array{T,N}`, où `N` est maintenant un paramètre de `ArrayContainer`

## [Performance of captured variable](@id man-performance-captured)

Considérez l'exemple suivant qui définit une fonction interne :

```julia
function abmult(r::Int)
    if r < 0
        r = -r
    end
    f = x -> x * r
    return f
end
```

La fonction `abmult` renvoie une fonction `f` qui multiplie son argument par la valeur absolue de `r`. La fonction interne assignée à `f` est appelée une "fermeture". Les fonctions internes sont également utilisées par le langage pour les blocs `do` et pour les expressions génératrices.

Ce style de code présente des défis de performance pour le langage. Le parseur, lorsqu'il le traduit en instructions de niveau inférieur, réorganise considérablement le code ci-dessus en extrayant la fonction interne dans un bloc de code séparé. Les variables "capturées" telles que `r` qui sont partagées par les fonctions internes et leur portée englobante sont également extraites dans une "boîte" allouée sur le tas, accessible à la fois aux fonctions internes et externes, car le langage spécifie que `r` dans la portée interne doit être identique à `r` dans la portée externe même après que la portée externe (ou une autre fonction interne) modifie `r`.

La discussion dans le paragraphe précédent faisait référence au "parseur", c'est-à-dire la phase de compilation qui se produit lorsque le module contenant `abmult` est d'abord chargé, par opposition à la phase ultérieure où il est d'abord invoqué. Le parseur ne "sait" pas que `Int` est un type fixe, ni que l'instruction `r = -r` transforme un `Int` en un autre `Int`. La magie de l'inférence de type se produit dans la phase ultérieure de la compilation.

Ainsi, le parseur ne sait pas que `r` a un type fixe (`Int`). ni que `r` ne change pas de valeur une fois la fonction interne créée (de sorte que la boîte est inutile). Par conséquent, le parseur émet du code pour une boîte qui contient un objet avec un type abstrait tel que `Any`, ce qui nécessite un dispatch de type à l'exécution pour chaque occurrence de `r`. Cela peut être vérifié en appliquant `@code_warntype` à la fonction ci-dessus. Tant la mise en boîte que le dispatch de type à l'exécution peuvent entraîner une perte de performance.

Si des variables capturées sont utilisées dans une section critique pour la performance du code, les conseils suivants aident à garantir que leur utilisation est performante. Tout d'abord, s'il est connu qu'une variable capturée ne change pas de type, cela peut être déclaré explicitement avec une annotation de type (sur la variable, et non sur le côté droit) :

```julia
function abmult2(r0::Int)
    r::Int = r0
    if r < 0
        r = -r
    end
    f = x -> x * r
    return f
end
```

L'annotation de type récupère partiellement les performances perdues en raison de la capture, car le parseur peut associer un type concret à l'objet dans la boîte. De plus, si la variable capturée n'a pas besoin d'être encapsulée du tout (car elle ne sera pas réaffectée après la création de la fermeture), cela peut être indiqué avec des blocs `let` comme suit.

```julia
function abmult3(r::Int)
    if r < 0
        r = -r
    end
    f = let r = r
            x -> x * r
    end
    return f
end
```

Le bloc `let` crée une nouvelle variable `r` dont la portée est uniquement la fonction interne. La deuxième technique récupère la performance complète du langage en présence de variables capturées. Notez que c'est un aspect en évolution rapide du compilateur, et il est probable que les futures versions ne nécessiteront pas ce degré d'annotation de la part du programmeur pour atteindre la performance. En attendant, certains paquets contribué par les utilisateurs comme [FastClosures](https://github.com/c42f/FastClosures.jl) automatisent l'insertion des instructions `let` comme dans `abmult3`.

## [Multithreading and linear algebra](@id man-multithreading-linear-algebra)

Cette section s'applique au code Julia multithreadé qui, dans chaque thread, effectue des opérations d'algèbre linéaire. En effet, ces opérations d'algèbre linéaire impliquent des appels BLAS / LAPACK, qui sont eux-mêmes multithreadés. Dans ce cas, il faut s'assurer que les cœurs ne sont pas surchargés en raison des deux types différents de multithreading.

Julia compile et utilise sa propre copie d'OpenBLAS pour l'algèbre linéaire, dont le nombre de threads est contrôlé par la variable d'environnement `OPENBLAS_NUM_THREADS`. Il peut être défini comme une option de ligne de commande lors du lancement de Julia, ou modifié pendant la session Julia avec `BLAS.set_num_threads(N)` (le sous-module `BLAS` est exporté par `using LinearAlgebra`). Sa valeur actuelle peut être consultée avec `BLAS.get_num_threads()`.

Lorsque l'utilisateur ne spécifie rien, Julia essaie de choisir une valeur raisonnable pour le nombre de threads OpenBLAS (par exemple, en fonction de la plateforme, de la version de Julia, etc.). Cependant, il est généralement recommandé de vérifier et de définir la valeur manuellement. Le comportement d'OpenBLAS est le suivant :

  * Si `OPENBLAS_NUM_THREADS=1`, OpenBLAS utilise le(s) thread(s) Julia appelant, c'est-à-dire qu'il "vit" dans le thread Julia qui exécute le calcul.
  * Si `OPENBLAS_NUM_THREADS=N>1`, OpenBLAS crée et gère sa propre pool de threads (`N` au total). Il n'y a qu'une seule pool de threads OpenBLAS partagée entre tous les threads Julia.

Lorsque vous démarrez Julia en mode multithreadé avec `JULIA_NUM_THREADS=X`, il est généralement recommandé de définir `OPENBLAS_NUM_THREADS=1`. Étant donné le comportement décrit ci-dessus, augmenter le nombre de threads BLAS à `N>1` peut facilement entraîner une performance pire, en particulier lorsque `N<<X`. Cependant, ceci n'est qu'une règle générale, et la meilleure façon de définir chaque nombre de threads est d'expérimenter sur votre application spécifique.

## [Alternative linear algebra backends](@id man-backends-linear-algebra)

En alternative à OpenBLAS, il existe plusieurs autres backends qui peuvent aider à améliorer les performances en algèbre linéaire. Des exemples notables incluent [MKL.jl](https://github.com/JuliaLinearAlgebra/MKL.jl) et [AppleAccelerate.jl](https://github.com/JuliaMath/AppleAccelerate.jl).

Ce sont des packages externes, donc nous ne les discuterons pas en détail ici. Veuillez vous référer à leur documentation respective (surtout parce qu'ils ont des comportements différents de ceux d'OpenBLAS en ce qui concerne le multithreading).

## Execution latency, package loading and package precompiling time

### Reducing time to first plot etc.

La première fois qu'une méthode julia est appelée, elle (et toutes les méthodes qu'elle appelle, ou celles qui peuvent être déterminées statiquement) sera compilée. La famille de macros [`@time`](@ref) illustre cela.

```
julia> foo() = rand(2,2) * rand(2,2)
foo (generic function with 1 method)

julia> @time @eval foo();
  0.252395 seconds (1.12 M allocations: 56.178 MiB, 2.93% gc time, 98.12% compilation time)

julia> @time @eval foo();
  0.000156 seconds (63 allocations: 2.453 KiB)
```

Notez que `@time @eval` est mieux pour mesurer le temps de compilation car sans [`@eval`](@ref), certaines compilations peuvent déjà être effectuées avant le début du chronométrage.

Lorsque vous développez un package, vous pouvez améliorer l'expérience de vos utilisateurs avec *la précompilation* afin que, lorsqu'ils utilisent le package, le code qu'ils utilisent soit déjà compilé. Pour précompiler le code du package de manière efficace, il est recommandé d'utiliser [`PrecompileTools.jl`](https://julialang.github.io/PrecompileTools.jl/stable/) pour exécuter une "charge de travail de précompilation" pendant le temps de précompilation qui est représentatif de l'utilisation typique du package, ce qui mettra en cache le code compilé natif dans le cache `pkgimage` du package, réduisant considérablement le "temps jusqu'à la première exécution" (souvent appelé TTFX) pour une telle utilisation.

Notez que [`PrecompileTools.jl`](https://julialang.github.io/PrecompileTools.jl/stable/) les charges de travail peuvent être désactivées et parfois configurées via les Préférences si vous ne souhaitez pas passer du temps supplémentaire à précompiler, ce qui peut être le cas lors du développement d'un package.

### Reducing package loading time

Garder le temps de chargement du package au minimum est généralement utile. Les bonnes pratiques générales pour les développeurs de packages incluent :

1. Réduisez vos dépendances à celles dont vous avez vraiment besoin. Envisagez d'utiliser [package extensions](@ref) pour soutenir l'interopérabilité avec d'autres packages sans alourdir vos dépendances essentielles.
2. Évitez d'utiliser les fonctions [`__init__()`](@ref) à moins qu'il n'y ait pas d'alternative, en particulier celles qui pourraient déclencher beaucoup de compilation ou qui prennent simplement beaucoup de temps à s'exécuter.
3. Où cela est possible, corrigez [invalidations](https://julialang.org/blog/2020/08/invalidations/) parmi vos dépendances et dans votre code de paquet.

L'outil [`@time_imports`](@ref) peut être utile dans le REPL pour examiner les facteurs ci-dessus.

```julia-repl
julia> @time @time_imports using Plots
      0.5 ms  Printf
     16.4 ms  Dates
      0.7 ms  Statistics
               ┌ 23.8 ms SuiteSparse_jll.__init__() 86.11% compilation time (100% recompilation)
     90.1 ms  SuiteSparse_jll 91.57% compilation time (82% recompilation)
      0.9 ms  Serialization
               ┌ 39.8 ms SparseArrays.CHOLMOD.__init__() 99.47% compilation time (100% recompilation)
    166.9 ms  SparseArrays 23.74% compilation time (100% recompilation)
      0.4 ms  Statistics → SparseArraysExt
      0.5 ms  TOML
      8.0 ms  Preferences
      0.3 ms  PrecompileTools
      0.2 ms  Reexport
... many deps omitted for example ...
      1.4 ms  Tar
               ┌ 73.8 ms p7zip_jll.__init__() 99.93% compilation time (100% recompilation)
     79.4 ms  p7zip_jll 92.91% compilation time (100% recompilation)
               ┌ 27.7 ms GR.GRPreferences.__init__() 99.77% compilation time (100% recompilation)
     43.0 ms  GR 64.26% compilation time (100% recompilation)
               ┌ 2.1 ms Plots.__init__() 91.80% compilation time (100% recompilation)
    300.9 ms  Plots 0.65% compilation time (100% recompilation)
  1.795602 seconds (3.33 M allocations: 190.153 MiB, 7.91% gc time, 39.45% compilation time: 97% of which was recompilation)

```

Remarquez que dans cet exemple, plusieurs packages sont chargés, certains avec des fonctions `__init__()`, dont certaines provoquent une compilation, tandis que d'autres entraînent une recompilation. La recompilation est causée par des packages antérieurs invalidant des méthodes, puis dans ces cas, lorsque les packages suivants exécutent leur fonction `__init__()`, certains rencontrent une recompilation avant que le code puisse être exécuté.

De plus, notez que l'extension `Statistics` `SparseArraysExt` a été activée car `SparseArrays` est dans l'arbre des dépendances. c'est-à-dire voir `0.4 ms  Statistics → SparseArraysExt`.

Ce rapport offre une bonne occasion de revoir si le coût du temps de chargement des dépendances vaut la fonctionnalité qu'il apporte. De plus, l'utilitaire `Pkg` `why` peut être utilisé pour signaler pourquoi une dépendance indirecte existe.

```
(CustomPackage) pkg> why FFMPEG_jll
  Plots → FFMPEG → FFMPEG_jll
  Plots → GR → GR_jll → FFMPEG_jll
```

ou pour voir les dépendances indirectes qu'un package apporte, vous pouvez `pkg> rm` le package, voir les dépendances qui sont supprimées du manifeste, puis revenir sur le changement avec `pkg> undo`.

Si le temps de chargement est dominé par des méthodes `__init__()` lentes ayant une compilation, une manière verbeuse d'identifier ce qui est en cours de compilation est d'utiliser les arguments julia `--trace-compile=stderr` qui rapportera une déclaration [`precompile`](@ref) chaque fois qu'une méthode est compilée. Par exemple, la configuration complète serait :

```
$ julia --startup-file=no --trace-compile=stderr
julia> @time @time_imports using CustomPackage
...
```

Notez le `--startup-file=no` qui aide à isoler le test des paquets que vous pourriez avoir dans votre `startup.jl`.

Une analyse plus approfondie des raisons de recompilation peut être réalisée avec le package [`SnoopCompile`](https://github.com/timholy/SnoopCompile.jl).
