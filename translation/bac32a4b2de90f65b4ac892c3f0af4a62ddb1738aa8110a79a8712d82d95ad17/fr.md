# Frequently Asked Questions

## General

### Is Julia named after someone or something?

Non.

### Why don't you compile Matlab/Python/R/… code to Julia?

Puisque de nombreuses personnes sont familières avec la syntaxe d'autres langages dynamiques, et que beaucoup de code a déjà été écrit dans ces langages, il est naturel de se demander pourquoi nous n'avons pas simplement intégré une interface Matlab ou Python dans un back-end Julia (ou "transpilé" du code vers Julia) afin d'obtenir tous les avantages de performance de Julia sans exiger que les programmeurs apprennent un nouveau langage. Simple, non ?

Le problème de base est qu'il n'y a *rien de spécial dans le compilateur de Julia* : nous utilisons un compilateur courant (LLVM) sans “ingrédients secrets” que d'autres développeurs de langages ne connaissent pas. En effet, le compilateur de Julia est à bien des égards beaucoup plus simple que ceux d'autres langages dynamiques (par exemple, PyPy ou LuaJIT). L'avantage de performance de Julia provient presque entièrement de son front-end : sa sémantique de langage permet à un [well-written Julia program](@ref man-performance-tips) de *donner plus d'opportunités au compilateur* pour générer un code et des agencements de mémoire efficaces. Si vous essayiez de compiler du code Matlab ou Python en Julia, notre compilateur serait limité par la sémantique de Matlab ou Python à produire un code pas meilleur que celui des compilateurs existants pour ces langages (et probablement pire). Le rôle clé de la sémantique est également la raison pour laquelle plusieurs compilateurs Python existants (comme Numba et Pythran) tentent seulement d'optimiser un petit sous-ensemble du langage (par exemple, les opérations sur les tableaux et scalaires Numpy), et pour ce sous-ensemble, ils font déjà au moins aussi bien que nous pour les mêmes sémantiques. Les personnes travaillant sur ces projets sont incroyablement intelligentes et ont accompli des choses étonnantes, mais adapter un compilateur à un langage qui a été conçu pour être interprété est un problème très difficile.

L'avantage de Julia est que la bonne performance n'est pas limitée à un petit sous-ensemble de types et d'opérations « intégrés », et l'on peut écrire du code générique de haut niveau qui fonctionne sur des types définis par l'utilisateur arbitraires tout en restant rapide et efficace en mémoire. Les types dans des langages comme Python ne fournissent tout simplement pas suffisamment d'informations au compilateur pour des capacités similaires, donc dès que vous utilisez ces langages comme interface de Julia, vous seriez bloqué.

Pour des raisons similaires, la traduction automatisée vers Julia générerait également typiquement un code illisible, lent et non idiomatique qui ne constituerait pas un bon point de départ pour un portage natif de Julia à partir d'un autre langage.

D'autre part, l'*interopérabilité* des langages est extrêmement utile : nous voulons exploiter le code existant de haute qualité dans d'autres langages depuis Julia (et vice versa) ! La meilleure façon de permettre cela n'est pas un transpileur, mais plutôt via des installations d'appel inter-langages faciles. Nous avons travaillé dur sur cela, depuis l'intrinsèque `ccall` intégré (pour appeler des bibliothèques C et Fortran) jusqu'aux paquets [JuliaInterop](https://github.com/JuliaInterop) qui connectent Julia à Python, Matlab, C++, et plus encore.

## [Public API](@id man-api)

### How does Julia define its public API?

Le [API](https://en.wikipedia.org/wiki/API) public de Julia est le comportement décrit dans la documentation des symboles publics de `Base` et des bibliothèques standard. Les fonctions, types et constantes ne font pas partie de l'API publique s'ils ne sont pas publics, même s'ils ont des docstrings ou sont décrits dans la documentation. De plus, seul le comportement documenté des symboles publics fait partie de l'API publique. Le comportement non documenté des symboles publics est interne.

Les symboles publics sont ceux marqués avec soit `public foo` soit `export foo`.

En d'autres termes :

  * Le comportement documenté des symboles publics fait partie de l'API publique.
  * Le comportement non documenté des symboles publics ne fait pas partie de l'API publique.
  * Le comportement documenté des symboles privés ne fait pas partie de l'API publique.
  * Le comportement non documenté des symboles privés ne fait pas partie de l'API publique.

Vous pouvez obtenir une liste complète des symboles publics d'un module avec `names(MyModule)`.

Les auteurs de packages sont encouragés à définir leur API publique de manière similaire.

Tout ce qui se trouve dans l'API publique de Julia est couvert par [SemVer](https://semver.org/) et ne sera donc pas supprimé ni ne subira de changements significatifs avant Julia 2.0.

### There is a useful undocumented function/type/constant. Can I use it?

Updating Julia may break your code if you use non-public API.  If the code is self-contained, it may be a good idea to copy it into your project.  If you want to rely on a complex non-public API, especially when using it from a stable package, it is a good idea to open an [issue](https://github.com/JuliaLang/julia/issues) or [pull request](https://github.com/JuliaLang/julia/pulls) to start a discussion for turning it into a public API.  However, we do not discourage the attempt to create packages that expose stable public interfaces while relying on non-public implementation details of Julia and buffering the differences across different Julia versions.

### The documentation is not accurate enough. Can I rely on the existing behavior?

Please open an [issue](https://github.com/JuliaLang/julia/issues) or [pull request](https://github.com/JuliaLang/julia/pulls) to start a discussion for turning the existing behavior into a public API.

## Sessions and the REPL

### How do I delete an object in memory?

Julia n'a pas d'analogue de la fonction `clear` de MATLAB ; une fois qu'un nom est défini dans une session Julia (techniquement, dans le module `Main`), il est toujours présent.

Si l'utilisation de la mémoire est votre préoccupation, vous pouvez toujours remplacer des objets par des objets qui consomment moins de mémoire. Par exemple, si `A` est un tableau de taille gigaoctet dont vous n'avez plus besoin, vous pouvez libérer la mémoire avec `A = nothing`. La mémoire sera libérée la prochaine fois que le ramasse-miettes s'exécutera ; vous pouvez forcer cela à se produire avec [`GC.gc()`](@ref Base.GC.gc). De plus, une tentative d'utilisation de `A` entraînera probablement une erreur, car la plupart des méthodes ne sont pas définies sur le type `Nothing`.

### How can I modify the declaration of a type in my session?

Peut-être que vous avez défini un type et que vous réalisez ensuite que vous devez ajouter un nouveau champ. Si vous essayez cela dans le REPL, vous obtenez l'erreur :

```
ERROR: invalid redefinition of constant MyType
```

Les types dans le module `Main` ne peuvent pas être redéfinis.

Bien que cela puisse être gênant lorsque vous développez un nouveau code, il existe une excellente solution de contournement. Les modules peuvent être remplacés en les redéfinissant, et donc si vous encapsulez tout votre nouveau code à l'intérieur d'un module, vous pouvez redéfinir des types et des constantes. Vous ne pouvez pas importer les noms de types dans `Main` et ensuite vous attendre à pouvoir les redéfinir là-bas, mais vous pouvez utiliser le nom du module pour résoudre la portée. En d'autres termes, pendant le développement, vous pourriez utiliser un flux de travail quelque chose comme ceci :

```julia
include("mynewcode.jl")              # this defines a module MyModule
obj1 = MyModule.ObjConstructor(a, b)
obj2 = MyModule.somefunction(obj1)
# Got an error. Change something in "mynewcode.jl"
include("mynewcode.jl")              # reload the module
obj1 = MyModule.ObjConstructor(a, b) # old objects are no longer valid, must reconstruct
obj2 = MyModule.somefunction(obj1)   # this time it worked!
obj3 = MyModule.someotherfunction(obj2, c)
...
```

## [Scripting](@id man-scripting)

### How do I check if the current file is being run as the main script?

Lorsque un fichier est exécuté en tant que script principal en utilisant `julia file.jl`, on peut vouloir activer des fonctionnalités supplémentaires comme la gestion des arguments de ligne de commande. Une façon de déterminer qu'un fichier est exécuté de cette manière est de vérifier si `abspath(PROGRAM_FILE) == @__FILE__` est `true`.

Cependant, il est recommandé de ne pas écrire des fichiers qui font à la fois office de script et de bibliothèque importable. Si l'on a besoin de fonctionnalités disponibles à la fois en tant que bibliothèque et en tant que script, il est préférable de les écrire en tant que bibliothèque, puis d'importer les fonctionnalités dans un script distinct.

### [How do I catch CTRL-C in a script?](@id catch-ctrl-c)

Exécuter un script Julia en utilisant `julia file.jl` ne lance pas [`InterruptException`](@ref) lorsque vous essayez de le terminer avec CTRL-C (SIGINT). Pour exécuter un certain code avant de terminer un script Julia, qui peut ou non être causé par CTRL-C, utilisez [`atexit`](@ref). Alternativement, vous pouvez utiliser `julia -e 'include(popfirst!(ARGS))' file.jl` pour exécuter un script tout en étant capable de capturer `InterruptException` dans le bloc [`try`](@ref). Notez qu'avec cette stratégie, [`PROGRAM_FILE`](@ref) ne sera pas défini.

### How do I pass options to `julia` using `#!/usr/bin/env`?

Passer des options à `julia` dans une ligne shebang, comme dans `#!/usr/bin/env julia --startup-file=no`, ne fonctionnera pas sur de nombreuses plateformes (BSD, macOS, Linux) où le noyau, contrairement au shell, ne divise pas les arguments aux caractères d'espace. L'option `env -S`, qui divise une chaîne d'argument unique en plusieurs arguments aux espaces, similaire à un shell, offre une solution simple :

```julia
#!/usr/bin/env -S julia --color=yes --startup-file=no
@show ARGS  # put any Julia code here
```

!!! note
    L'option `env -S` est apparue dans FreeBSD 6.0 (2005), macOS Sierra (2016) et GNU/Linux coreutils 8.30 (2018).


### Why doesn't `run` support `*` or pipes for scripting external programs?

La fonction [`run`](@ref) de Julia lance des programmes externes *directement*, sans invoquer [operating-system shell](https://en.wikipedia.org/wiki/Shell_(computing)) (contrairement à la fonction `system("...")` dans d'autres langages comme Python, R ou C). Cela signifie que `run` ne réalise pas d'expansion de caractères génériques `*` (["globbing"](https://en.wikipedia.org/wiki/Glob_(programming))), ni n'interprète [shell pipelines](https://en.wikipedia.org/wiki/Pipeline_(Unix)) comme `|` ou `>`.

Vous pouvez toujours faire du globbing et des pipelines en utilisant les fonctionnalités de Julia, cependant. Par exemple, la fonction intégrée [`pipeline`](@ref) vous permet de chaîner des programmes et des fichiers externes, similaire aux pipes de shell, et le [Glob.jl package](https://github.com/vtjnash/Glob.jl) implémente un globbing compatible POSIX.

Vous pouvez, bien sûr, exécuter des programmes via le shell en passant explicitement un shell et une chaîne de commande à `run`, par exemple ```run(`sh -c "ls > files.txt"`)``` pour utiliser le Unix [Bourne shell](https://en.wikipedia.org/wiki/Bourne_shell), mais vous devriez généralement préférer le script pur en Julia comme ```run(pipeline(`ls`, "files.txt"))```. La raison pour laquelle nous évitons le shell par défaut est que [shelling out sucks](https://julialang.org/blog/2012/03/shelling-out-sucks/): lancer des processus via le shell est lent, fragile face à la citation de caractères spéciaux, a une mauvaise gestion des erreurs et pose des problèmes de portabilité. (Les développeurs Python en sont venus à une [similar conclusion](https://www.python.org/dev/peps/pep-0324/#motivation).)

## Variables and Assignments

### Why am I getting `UndefVarError` from a simple loop?

Vous pourriez avoir quelque chose comme :

```
x = 0
while x < 10
    x += 1
end
```

et remarquez que cela fonctionne bien dans un environnement interactif (comme le REPL de Julia), mais donne ```UndefVarError: `x` not defined``` lorsque vous essayez de l'exécuter dans un script ou un autre fichier. Ce qui se passe, c'est que Julia exige généralement que vous **soyez explicite sur l'attribution aux variables globales dans un contexte local**.

Ici, `x` est une variable globale, `while` définit un [local scope](@ref scope-of-variables), et `x += 1` est une affectation à une variable globale dans ce contexte local.

Comme mentionné ci-dessus, Julia (version 1.5 ou ultérieure) vous permet d'omettre le mot-clé `global` pour le code dans le REPL (et de nombreux autres environnements interactifs), afin de simplifier l'exploration (par exemple, copier-coller du code d'une fonction pour l'exécuter de manière interactive). Cependant, une fois que vous passez au code dans des fichiers, Julia nécessite une approche plus disciplinée des variables globales. Vous avez au moins trois options :

1. Mettez le code dans une fonction (de sorte que `x` soit une variable *locale* dans une fonction). En général, il est bon de faire de l'ingénierie logicielle d'utiliser des fonctions plutôt que des scripts globaux (cherchez en ligne "pourquoi les variables globales sont mauvaises" pour voir de nombreuses explications). En Julia, les variables globales sont également [slow](@ref man-performance-tips).
2. Enveloppez le code dans un bloc [`let`](@ref). (Cela rend `x` une variable locale dans l'instruction `let ... end`, éliminant ainsi à nouveau le besoin de `global`).
3. Marquez explicitement `x` comme `global` à l'intérieur de la portée locale avant de lui assigner une valeur, par exemple écrivez `global x += 1`.

Plus d'explications peuvent être trouvées dans la section du manuel [on soft scope](@ref on-soft-scope).

## Functions

### I passed an argument `x` to a function, modified it inside that function, but on the outside, the variable `x` is still unchanged. Why?

Supposons que vous appeliez une fonction comme ceci :

```jldoctest
julia> x = 10
10

julia> function change_value!(y)
           y = 17
       end
change_value! (generic function with 1 method)

julia> change_value!(x)
17

julia> x # x is unchanged!
10
```

En Julia, la liaison d'une variable `x` ne peut pas être modifiée en passant `x` comme argument à une fonction. Lors de l'appel de `change_value!(x)` dans l'exemple ci-dessus, `y` est une variable nouvellement créée, initialement liée à la valeur de `x`, c'est-à-dire `10` ; ensuite, `y` est réassignée à la constante `17`, tandis que la variable `x` de la portée extérieure reste intacte.

Cependant, si `x` est lié à un objet de type `Array` (ou tout autre type *mutable*). De l'intérieur de la fonction, vous ne pouvez pas "délier" `x` de ce tableau, mais vous *pouvez* changer son contenu. Par exemple :

```jldoctest
julia> x = [1,2,3]
3-element Vector{Int64}:
 1
 2
 3

julia> function change_array!(A)
           A[1] = 5
       end
change_array! (generic function with 1 method)

julia> change_array!(x)
5

julia> x
3-element Vector{Int64}:
 5
 2
 3
```

Ici, nous avons créé une fonction `change_array!`, qui assigne `5` au premier élément du tableau passé (lié à `x` au site d'appel, et lié à `A` dans la fonction). Remarquez qu'après l'appel de la fonction, `x` est toujours lié au même tableau, mais le contenu de ce tableau a changé : les variables `A` et `x` étaient des liaisons distinctes faisant référence au même objet `Array` mutable.

### Can I use `using` or `import` inside a function?

Non, vous n'êtes pas autorisé à avoir une déclaration `using` ou `import` à l'intérieur d'une fonction. Si vous souhaitez importer un module mais n'utiliser ses symboles qu'à l'intérieur d'une fonction spécifique ou d'un ensemble de fonctions, vous avez deux options :

1. Utilisez `import` :

    ```julia
    import Foo
    function bar(...)
        # ... refer to Foo symbols via Foo.baz ...
    end
    ```

    Cela charge le module `Foo` et définit une variable `Foo` qui fait référence au module, mais n'importe aucun des autres symboles du module dans l'espace de noms actuel. Vous faites référence aux symboles `Foo` par leurs noms qualifiés `Foo.bar`, etc.
2. Enveloppez votre fonction dans un module :

    ```julia
    module Bar
    export bar
    using Foo
    function bar(...)
        # ... refer to Foo.baz as simply baz ....
    end
    end
    using Bar
    ```

    Cela importe tous les symboles de `Foo`, mais uniquement à l'intérieur du module `Bar`.

### What does the `...` operator do?

#### The two uses of the `...` operator: slurping and splatting

De nombreux nouveaux utilisateurs de Julia trouvent l'utilisation de l'opérateur `...` déroutante. Une partie de ce qui rend l'opérateur `...` déroutant est qu'il signifie deux choses différentes selon le contexte.

#### `...` combines many arguments into one argument in function definitions

Dans le contexte des définitions de fonctions, l'opérateur `...` est utilisé pour combiner de nombreux arguments différents en un seul argument. Cette utilisation de `...` pour combiner de nombreux arguments différents en un seul argument est appelée slurping :

```jldoctest
julia> function printargs(args...)
           println(typeof(args))
           for (i, arg) in enumerate(args)
               println("Arg #$i = $arg")
           end
       end
printargs (generic function with 1 method)

julia> printargs(1, 2, 3)
Tuple{Int64, Int64, Int64}
Arg #1 = 1
Arg #2 = 2
Arg #3 = 3
```

Si Julia était un langage qui utilisait plus librement les caractères ASCII, l'opérateur de slurping aurait pu être écrit comme `<-...` au lieu de `...`.

#### `...` splits one argument into many different arguments in function calls

Contrairement à l'utilisation de l'opérateur `...` pour désigner l'absorption de nombreux arguments différents en un seul argument lors de la définition d'une fonction, l'opérateur `...` est également utilisé pour faire en sorte qu'un seul argument de fonction soit divisé en de nombreux arguments différents lorsqu'il est utilisé dans le contexte d'un appel de fonction. Cette utilisation de `...` est appelée splatting :

```jldoctest
julia> function threeargs(a, b, c)
           println("a = $a::$(typeof(a))")
           println("b = $b::$(typeof(b))")
           println("c = $c::$(typeof(c))")
       end
threeargs (generic function with 1 method)

julia> x = [1, 2, 3]
3-element Vector{Int64}:
 1
 2
 3

julia> threeargs(x...)
a = 1::Int64
b = 2::Int64
c = 3::Int64
```

Si Julia était un langage qui utilisait plus librement les caractères ASCII, l'opérateur de splatting aurait pu être écrit comme `...->` au lieu de `...`.

### What is the return value of an assignment?

L'opérateur `=` renvoie toujours le côté droit, donc :

```jldoctest
julia> function threeint()
           x::Int = 3.0
           x # returns variable x
       end
threeint (generic function with 1 method)

julia> function threefloat()
           x::Int = 3.0 # returns 3.0
       end
threefloat (generic function with 1 method)

julia> threeint()
3

julia> threefloat()
3.0
```

et de même :

```jldoctest
julia> function twothreetup()
           x, y = [2, 3] # assigns 2 to x and 3 to y
           x, y # returns a tuple
       end
twothreetup (generic function with 1 method)

julia> function twothreearr()
           x, y = [2, 3] # returns an array
       end
twothreearr (generic function with 1 method)

julia> twothreetup()
(2, 3)

julia> twothreearr()
2-element Vector{Int64}:
 2
 3
```

## Types, type declarations, and constructors

### [What does "type-stable" mean?](@id man-type-stability)

Cela signifie que le type de la sortie est prévisible à partir des types des entrées. En particulier, cela signifie que le type de la sortie ne peut pas varier en fonction des *valeurs* des entrées. Le code suivant n'est *pas* stable en termes de type :

```jldoctest
julia> function unstable(flag::Bool)
           if flag
               return 1
           else
               return 1.0
           end
       end
unstable (generic function with 1 method)
```

Il renvoie soit un `Int`, soit un [`Float64`](@ref) en fonction de la valeur de son argument. Comme Julia ne peut pas prédire le type de retour de cette fonction à la compilation, tout calcul qui l'utilise doit être capable de gérer des valeurs des deux types, ce qui rend difficile la production de code machine rapide.

### [Why does Julia give a `DomainError` for certain seemingly-sensible operations?](@id faq-domain-errors)

Certain operations ont un sens mathématique mais entraînent des erreurs :

```jldoctest
julia> sqrt(-2.0)
ERROR: DomainError with -2.0:
sqrt was called with a negative real argument but will only return a complex result if called with a complex argument. Try sqrt(Complex(x)).
Stacktrace:
[...]
```

Ce comportement est une conséquence inconvenante de l'exigence de stabilité de type. Dans le cas de [`sqrt`](@ref), la plupart des utilisateurs souhaitent que `sqrt(2.0)` renvoie un nombre réel, et seraient mécontents s'il produisait le nombre complexe `1.4142135623730951 + 0.0im`. On pourrait écrire la fonction `4d61726b646f776e2e436f64652822222c2022737172742229_40726566` pour passer à une sortie à valeur complexe uniquement lorsqu'un nombre négatif est passé (ce que fait `4d61726b646f776e2e436f64652822222c2022737172742229_40726566` dans d'autres langages), mais alors le résultat ne serait pas [type-stable](@ref man-type-stability) et la fonction `4d61726b646f776e2e436f64652822222c2022737172742229_40726566` aurait de mauvaises performances.

Dans ces cas et d'autres, vous pouvez obtenir le résultat souhaité en choisissant un *type d'entrée* qui exprime votre volonté d'accepter un *type de sortie* dans lequel le résultat peut être représenté :

```jldoctest
julia> sqrt(-2.0+0im)
0.0 + 1.4142135623730951im
```

### How can I constrain or compute type parameters?

Les paramètres d'un [parametric type](@ref Parametric-Types) peuvent contenir soit des types, soit des valeurs de bits, et le type lui-même choisit comment il utilise ces paramètres. Par exemple, `Array{Float64, 2}` est paramétré par le type `Float64` pour exprimer son type d'élément et la valeur entière `2` pour exprimer son nombre de dimensions. Lorsque vous définissez votre propre type paramétrique, vous pouvez utiliser des contraintes de sous-type pour déclarer qu'un certain paramètre doit être un sous-type ([`<:`](@ref)) d'un certain type abstrait ou d'un paramètre de type précédent. Il n'y a cependant pas de syntaxe dédiée pour déclarer qu'un paramètre doit être une *valeur* d'un type donné — c'est-à-dire que vous ne pouvez pas déclarer directement qu'un paramètre de type dimensionnel [`isa`](@ref) `Int` dans la définition de `struct`, par exemple. De même, vous ne pouvez pas effectuer de calculs (y compris des choses simples comme l'addition ou la soustraction) sur des paramètres de type. Au lieu de cela, ces sortes de contraintes et de relations peuvent être exprimées par le biais de paramètres de type supplémentaires qui sont calculés et appliqués dans le [constructors](@ref man-constructors) du type.

En tant qu'exemple, considérez

```julia
struct ConstrainedType{T,N,N+1} # NOTE: INVALID SYNTAX
    A::Array{T,N}
    B::Array{T,N+1}
end
```

où l'utilisateur souhaiterait faire en sorte que le troisième paramètre de type soit toujours le deuxième plus un. Cela peut être implémenté avec un paramètre de type explicite qui est vérifié par un [inner constructor method](@ref man-inner-constructor-methods) (où il peut être combiné avec d'autres vérifications) :

```julia
struct ConstrainedType{T,N,M}
    A::Array{T,N}
    B::Array{T,M}
    function ConstrainedType(A::Array{T,N}, B::Array{T,M}) where {T,N,M}
        N + 1 == M || throw(ArgumentError("second argument should have one more axis" ))
        new{T,N,M}(A, B)
    end
end
```

Cette vérification est généralement *sans coût*, car le compilateur peut omettre la vérification des types concrets valides. Si le deuxième argument est également calculé, il peut être avantageux de fournir un [outer constructor method](@ref man-outer-constructor-methods) qui effectue ce calcul :

```julia
ConstrainedType(A) = ConstrainedType(A, compute_B(A))
```

### [Why does Julia use native machine integer arithmetic?](@id faq-integer-arithmetic)

Julia utilise l'arithmétique machine pour les calculs entiers. Cela signifie que la plage des valeurs `Int` est limitée et se replie à chaque extrémité, de sorte que l'addition, la soustraction et la multiplication d'entiers peuvent provoquer un débordement ou un sous-débordement, ce qui peut conduire à des résultats qui peuvent être déconcertants au début :

```jldoctest
julia> x = typemax(Int)
9223372036854775807

julia> y = x+1
-9223372036854775808

julia> z = -y
-9223372036854775808

julia> 2*z
0
```

Il est clair que cela est loin du comportement des entiers mathématiques, et vous pourriez penser qu'il est moins qu'idéal pour un langage de programmation de haut niveau d'exposer cela à l'utilisateur. Cependant, pour le travail numérique où l'efficacité et la transparence sont primordiales, les alternatives sont pires.

Une alternative à considérer serait de vérifier chaque opération entière pour un dépassement et de promouvoir les résultats vers des types d'entiers plus grands tels que [`Int128`](@ref) ou [`BigInt`](@ref) en cas de dépassement. Malheureusement, cela introduit une surcharge majeure sur chaque opération entière (pensez à l'incrémentation d'un compteur de boucle) – cela nécessite d'émettre du code pour effectuer des vérifications de dépassement à l'exécution après les instructions arithmétiques et des branches pour gérer les dépassements potentiels. Pire encore, cela rendrait chaque calcul impliquant des entiers instable en termes de type. Comme nous l'avons mentionné ci-dessus, [type-stability is crucial](@ref man-type-stability) pour une génération efficace de code performant. Si vous ne pouvez pas compter sur les résultats des opérations entières étant des entiers, il est impossible de générer un code rapide et simple comme le font les compilateurs C et Fortran.

Une variation de cette approche, qui évite l'apparence d'instabilité de type, consiste à fusionner les types `Int` et [`BigInt`](@ref) en un seul type entier hybride, qui change en interne de représentation lorsque le résultat ne rentre plus dans la taille d'un entier machine. Bien que cela évite superficiellement l'instabilité de type au niveau du code Julia, cela balaie simplement le problème sous le tapis en transférant toutes les mêmes difficultés au code C qui implémente ce type entier hybride. Cette approche *peut* fonctionner et peut même être rendue assez rapide dans de nombreux cas, mais présente plusieurs inconvénients. Un problème est que la représentation en mémoire des entiers et des tableaux d'entiers ne correspond plus à la représentation naturelle utilisée par C, Fortran et d'autres langages avec des entiers machine natifs. Ainsi, pour interagir avec ces langages, nous devrions finalement introduire des types d'entiers natifs de toute façon. Toute représentation non bornée des entiers ne peut pas avoir un nombre fixe de bits, et ne peut donc pas être stockée en ligne dans un tableau avec des emplacements de taille fixe – les grandes valeurs entières nécessiteront toujours un stockage séparé alloué sur le tas. Et bien sûr, peu importe à quel point une implémentation d'entier hybride est astucieuse, il y a toujours des pièges de performance – des situations où la performance se dégrade de manière inattendue. La représentation complexe, le manque d'interopérabilité avec C et Fortran, l'incapacité à représenter des tableaux d'entiers sans stockage supplémentaire sur le tas, et les caractéristiques de performance imprévisibles font même des implémentations d'entiers hybrides les plus astucieuses un mauvais choix pour un travail numérique haute performance.

Une alternative à l'utilisation d'entiers hybrides ou à la promotion en BigInts est d'utiliser l'arithmétique entière saturante, où l'ajout à la plus grande valeur entière la laisse inchangée et de même pour la soustraction de la plus petite valeur entière. C'est précisément ce que fait Matlab™ :

```
>> int64(9223372036854775807)

ans =

  9223372036854775807

>> int64(9223372036854775807) + 1

ans =

  9223372036854775807

>> int64(-9223372036854775808)

ans =

 -9223372036854775808

>> int64(-9223372036854775808) - 1

ans =

 -9223372036854775808
```

À première vue, cela semble raisonnable puisque 9223372036854775807 est beaucoup plus proche de 9223372036854775808 que -9223372036854775808 ne l'est et les entiers sont toujours représentés avec une taille fixe d'une manière naturelle qui est compatible avec C et Fortran. Cependant, l'arithmétique des entiers saturés est profondément problématique. Le premier et le plus évident problème est que ce n'est pas ainsi que fonctionne l'arithmétique des entiers en machine, donc la mise en œuvre d'opérations saturées nécessite d'émettre des instructions après chaque opération d'entier en machine pour vérifier les débordements ou les sous-débordements et remplacer le résultat par [`typemin(Int)`](@ref) ou [`typemax(Int)`](@ref) selon le cas. Cela seul étend chaque opération entière d'une seule instruction rapide à une demi-douzaine d'instructions, probablement y compris des branches. Aïe. Mais cela devient pire – l'arithmétique des entiers saturés n'est pas associative. Considérons ce calcul Matlab :

```
>> n = int64(2)^62
4611686018427387904

>> n + (n - 1)
9223372036854775807

>> (n + n) - 1
9223372036854775806
```

Cela rend difficile l'écriture de nombreux algorithmes d'entiers de base, car de nombreuses techniques courantes dépendent du fait que l'addition machine avec débordement *est* associative. Considérons la recherche du point médian entre les valeurs entières `lo` et `hi` en Julia en utilisant l'expression `(lo + hi) >>> 1` :

```jldoctest
julia> n = 2^62
4611686018427387904

julia> (n + 2n) >>> 1
6917529027641081856
```

Vous voyez ? Aucun problème. C'est le point médian correct entre 2^62 et 2^63, malgré le fait que `n + 2n` soit -4611686018427387904. Essayez maintenant dans Matlab :

```
>> (n + 2*n)/2

ans =

  4611686018427387904
```

Oups. Ajouter un opérateur `>>>` à Matlab ne serait pas utile, car la saturation qui se produit lors de l'addition de `n` et `2n` a déjà détruit l'information nécessaire pour calculer le point médian correct.

Non seulement le manque d'associativité est malheureux pour les programmeurs qui ne peuvent pas s'y fier pour des techniques comme celle-ci, mais cela contrecarrie également presque tout ce que les compilateurs pourraient vouloir faire pour optimiser l'arithmétique entière. Par exemple, puisque les entiers de Julia utilisent l'arithmétique entière normale de la machine, LLVM est libre d'optimiser de manière agressive de petites fonctions simples comme `f(k) = 5k-1`. Le code machine pour cette fonction est juste ceci :

```julia-repl
julia> code_native(f, Tuple{Int})
  .text
Filename: none
  pushq %rbp
  movq  %rsp, %rbp
Source line: 1
  leaq  -1(%rdi,%rdi,4), %rax
  popq  %rbp
  retq
  nopl  (%rax,%rax)
```

Le corps réel de la fonction est une seule instruction `leaq`, qui calcule la multiplication entière et l'addition en une seule fois. Cela est encore plus bénéfique lorsque `f` est intégré dans une autre fonction :

```julia-repl
julia> function g(k, n)
           for i = 1:n
               k = f(k)
           end
           return k
       end
g (generic function with 1 methods)

julia> code_native(g, Tuple{Int,Int})
  .text
Filename: none
  pushq %rbp
  movq  %rsp, %rbp
Source line: 2
  testq %rsi, %rsi
  jle L26
  nopl  (%rax)
Source line: 3
L16:
  leaq  -1(%rdi,%rdi,4), %rdi
Source line: 2
  decq  %rsi
  jne L16
Source line: 5
L26:
  movq  %rdi, %rax
  popq  %rbp
  retq
  nop
```

Puisque l'appel à `f` est intégré, le corps de la boucle se retrouve être juste une seule instruction `leaq`. Ensuite, considérons ce qui se passe si nous fixons le nombre d'itérations de la boucle :

```julia-repl
julia> function g(k)
           for i = 1:10
               k = f(k)
           end
           return k
       end
g (generic function with 2 methods)

julia> code_native(g,(Int,))
  .text
Filename: none
  pushq %rbp
  movq  %rsp, %rbp
Source line: 3
  imulq $9765625, %rdi, %rax    # imm = 0x9502F9
  addq  $-2441406, %rax         # imm = 0xFFDABF42
Source line: 5
  popq  %rbp
  retq
  nopw  %cs:(%rax,%rax)
```

Parce que le compilateur sait que l'addition et la multiplication des entiers sont associatives et que la multiplication se distribue sur l'addition – ce qui n'est pas vrai pour l'arithmétique saturée – il peut optimiser l'ensemble de la boucle en une simple multiplication et une addition. L'arithmétique saturée contrecarrer complètement ce type d'optimisation, car l'associativité et la distributivité peuvent échouer à chaque itération de la boucle, entraînant des résultats différents selon l'itération à laquelle l'échec se produit. Le compilateur peut dérouler la boucle, mais il ne peut pas réduire algébriquement plusieurs opérations en moins d'opérations équivalentes.

L'alternative la plus raisonnable à l'overflow silencieux de l'arithmétique entière est de faire de l'arithmétique vérifiée partout, en levant des erreurs lorsque les additions, soustractions et multiplications débordent, produisant des valeurs qui ne sont pas correctes. Dans ce [blog post](https://danluu.com/integer-overflow/), Dan Luu analyse cela et constate que, plutôt que le coût trivial que cette approche devrait théoriquement avoir, elle finit par avoir un coût substantiel en raison des compilateurs (LLVM et GCC) qui n'optimisent pas gracieusement autour des vérifications de débordement ajoutées. Si cela s'améliore à l'avenir, nous pourrions envisager de par défaut à l'arithmétique entière vérifiée dans Julia, mais pour l'instant, nous devons vivre avec la possibilité de débordement.

En attendant, des opérations entières sûres contre le débordement peuvent être réalisées grâce à l'utilisation de bibliothèques externes telles que [SaferIntegers.jl](https://github.com/JeffreySarnoff/SaferIntegers.jl). Notez que, comme mentionné précédemment, l'utilisation de ces bibliothèques augmente considérablement le temps d'exécution du code utilisant les types entiers vérifiés. Cependant, pour une utilisation limitée, cela pose beaucoup moins de problèmes que si cela était utilisé pour toutes les opérations entières. Vous pouvez suivre l'état de la discussion [here](https://github.com/JuliaLang/julia/issues/855).

### What are the possible causes of an `UndefVarError` during remote execution?

Comme l'erreur l'indique, une cause immédiate d'un `UndefVarError` sur un nœud distant est qu'un lien portant ce nom n'existe pas. Explorons quelques-unes des causes possibles.

```julia-repl
julia> module Foo
           foo() = remotecall_fetch(x->x, 2, "Hello")
       end

julia> Foo.foo()
ERROR: On worker 2:
UndefVarError: `Foo` not defined in `Main`
Stacktrace:
[...]
```

La fermeture `x->x` porte une référence à `Foo`, et puisque `Foo` n'est pas disponible sur le nœud 2, une `UndefVarError` est levée.

Les variables globales sous des modules autres que `Main` ne sont pas sérialisées par valeur vers le nœud distant. Seule une référence est envoyée. Les fonctions qui créent des liaisons globales (sauf sous `Main`) peuvent provoquer un `UndefVarError` plus tard.

```julia-repl
julia> @everywhere module Foo
           function foo()
               global gvar = "Hello"
               remotecall_fetch(()->gvar, 2)
           end
       end

julia> Foo.foo()
ERROR: On worker 2:
UndefVarError: `gvar` not defined in `Main.Foo`
Stacktrace:
[...]
```

Dans l'exemple ci-dessus, `@everywhere module Foo` a défini `Foo` sur tous les nœuds. Cependant, l'appel à `Foo.foo()` a créé un nouveau lien global `gvar` sur le nœud local, mais cela n'a pas été trouvé sur le nœud 2, ce qui a entraîné une erreur `UndefVarError`.

Notez que cela ne s'applique pas aux globals créés sous le module `Main`. Les globals sous le module `Main` sont sérialisés et de nouveaux liens créés sous `Main` sur le nœud distant.

```julia-repl
julia> gvar_self = "Node1"
"Node1"

julia> remotecall_fetch(()->gvar_self, 2)
"Node1"

julia> remotecall_fetch(varinfo, 2)
name          size summary
––––––––– –––––––– –––––––
Base               Module
Core               Module
Main               Module
gvar_self 13 bytes String
```

Cela ne s'applique pas aux déclarations de `function` ou de `struct`. Cependant, les fonctions anonymes liées aux variables globales sont sérialisées comme on peut le voir ci-dessous.

```julia-repl
julia> bar() = 1
bar (generic function with 1 method)

julia> remotecall_fetch(bar, 2)
ERROR: On worker 2:
UndefVarError: `#bar` not defined in `Main`
[...]

julia> anon_bar  = ()->1
(::#21) (generic function with 1 method)

julia> remotecall_fetch(anon_bar, 2)
1
```

## Troubleshooting "method not matched": parametric type invariance and `MethodError`s

### Why doesn't it work to declare `foo(bar::Vector{Real}) = 42` and then call `foo([1])`?

Comme vous le verrez si vous essayez cela, le résultat est une `MethodError` :

```jldoctest
julia> foo(x::Vector{Real}) = 42
foo (generic function with 1 method)

julia> foo([1])
ERROR: MethodError: no method matching foo(::Vector{Int64})
The function `foo` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  foo(!Matched::Vector{Real})
   @ Main none:1

Stacktrace:
[...]
```

C'est parce que `Vector{Real}` n'est pas un supertype de `Vector{Int}` ! Vous pouvez résoudre ce problème avec quelque chose comme `foo(bar::Vector{T}) where {T<:Real}` (ou la forme courte `foo(bar::Vector{<:Real})` si le paramètre statique `T` n'est pas nécessaire dans le corps de la fonction). Le `T` est un caractère générique : vous spécifiez d'abord qu'il doit être un sous-type de Real, puis vous spécifiez que la fonction prend un Vector avec des éléments de ce type.

Ce même problème s'applique à tout type composite `Comp`, pas seulement à `Vector`. Si `Comp` a un paramètre déclaré de type `Y`, alors un autre type `Comp2` avec un paramètre de type `X<:Y` n'est pas un sous-type de `Comp`. C'est l'invariance de type (en revanche, Tuple est covariant dans ses paramètres). Voir [Parametric Composite Types](@ref man-parametric-composite-types) pour plus d'explications à ce sujet.

### Why does Julia use `*` for string concatenation? Why not `+` or something else?

Le [main argument](@ref man-concatenation) contre `+` est que la concaténation de chaînes n'est pas commutative, tandis que `+` est généralement utilisé comme un opérateur commutatif. Bien que la communauté Julia reconnaisse que d'autres langages utilisent des opérateurs différents et que `*` puisse être inconnu pour certains utilisateurs, cela communique certaines propriétés algébriques.

Notez que vous pouvez également utiliser `string(...)` pour concaténer des chaînes (et d'autres valeurs converties en chaînes) ; de même, `repeat` peut être utilisé à la place de `^` pour répéter des chaînes. Le [interpolation syntax](@ref string-interpolation) est également utile pour construire des chaînes.

## Packages and Modules

### What is the difference between "using" and "import"?

Il existe plusieurs différences entre `using` et `import` (voir le [Modules section](https://docs.julialang.org/en/v1/manual/modules/#modules)), mais il y a une différence importante qui peut ne pas sembler intuitive à première vue, et en surface (c'est-à-dire au niveau de la syntaxe), elle peut sembler très mineure. Lors du chargement de modules avec `using`, vous devez dire `function Foo.bar(...` pour étendre la fonction `bar` du module `Foo` avec une nouvelle méthode, mais avec `import Foo.bar`, vous n'avez besoin de dire que `function bar(...` et cela étend automatiquement la fonction `bar` du module `Foo`.

La raison pour laquelle cela est suffisamment important pour avoir une syntaxe distincte est que vous ne voulez pas accidentellement étendre une fonction que vous ne saviez pas qu'elle existait, car cela pourrait facilement causer un bug. Cela est le plus susceptible de se produire avec une méthode qui prend un type commun comme une chaîne de caractères ou un entier, car vous et l'autre module pourriez définir une méthode pour gérer un tel type commun. Si vous utilisez `import`, alors vous remplacerez l'implémentation de l'autre module de `bar(s::AbstractString)` par votre nouvelle implémentation, qui pourrait facilement faire quelque chose de complètement différent (et casser toutes/plusieurs utilisations futures des autres fonctions dans le module Foo qui dépendent de l'appel de bar).

## Nothingness and missing values

### [How does "null", "nothingness" or "missingness" work in Julia?](@id faq-nothing)

Contrairement à de nombreuses langues (par exemple, C et Java), les objets Julia ne peuvent pas être "null" par défaut. Lorsqu'une référence (variable, champ d'objet ou élément de tableau) n'est pas initialisée, y accéder déclenchera immédiatement une erreur. Cette situation peut être détectée en utilisant les fonctions [`isdefined`](@ref) ou [`isassigned`](@ref Base.isassigned).

Certaines fonctions sont utilisées uniquement pour leurs effets secondaires et n'ont pas besoin de retourner une valeur. Dans ces cas, la convention est de retourner la valeur `nothing`, qui est simplement un objet singleton de type `Nothing`. C'est un type ordinaire sans champs ; il n'y a rien de spécial à son sujet, sauf pour cette convention, et le REPL ne imprime rien pour cela. Certaines constructions de langage qui n'auraient autrement pas de valeur renvoient également `nothing`, par exemple `if false; end`.

Pour les situations où une valeur `x` de type `T` n'existe que parfois, le type `Union{T, Nothing}` peut être utilisé pour les arguments de fonction, les champs d'objet et les types d'éléments de tableau comme l'équivalent de [`Nullable`, `Option` or `Maybe`](https://en.wikipedia.org/wiki/Nullable_type) dans d'autres langages. Si la valeur elle-même peut être `nothing` (notamment lorsque `T` est `Any`), le type `Union{Some{T}, Nothing}` est plus approprié puisque `x == nothing` indique alors l'absence d'une valeur, et `x == Some(nothing)` indique la présence d'une valeur égale à `nothing`. La fonction [`something`](@ref) permet de déballer les objets `Some` et d'utiliser une valeur par défaut au lieu des arguments `nothing`. Notez que le compilateur est capable de générer un code efficace lorsqu'il travaille avec des arguments ou des champs `Union{T, Nothing}`.

Pour représenter les données manquantes dans le sens statistique (`NA` en R ou `NULL` en SQL), utilisez l'objet [`missing`](@ref). Consultez la section [`Missing Values`](@ref missing) pour plus de détails.

Dans certaines langues, le tuple vide (`()`) est considéré comme la forme canonique du néant. Cependant, en julia, il est préférable de le considérer simplement comme un tuple ordinaire qui contient zéro valeur.

Le type vide (ou "type de fond"), écrit comme `Union{}` (un type d'union vide), est un type sans valeurs et sans sous-types (sauf lui-même). Vous n'aurez généralement pas besoin d'utiliser ce type.

## Memory

### Why does `x += y` allocate memory when `x` and `y` are arrays?

En Julia, `x += y` est remplacé lors de la réduction par `x = x + y`. Pour les tableaux, cela a pour conséquence que, plutôt que de stocker le résultat à la même adresse mémoire que `x`, cela alloue un nouveau tableau pour stocker le résultat. Si vous préférez muter `x`, utilisez `x .+= y` pour mettre à jour chaque élément individuellement.

Bien que ce comportement puisse surprendre certains, le choix est délibéré. La principale raison est la présence d'objets immuables dans Julia, qui ne peuvent pas changer leur valeur une fois créés. En effet, un nombre est un objet immuable ; les instructions `x = 5; x += 1` ne modifient pas la signification de `5`, elles modifient la valeur liée à `x`. Pour un immuable, la seule façon de changer la valeur est de le réaffecter.

Pour amplifier un peu plus, considérez la fonction suivante :

```julia
function power_by_squaring(x, n::Int)
    ispow2(n) || error("This implementation only works for powers of 2")
    while n >= 2
        x *= x
        n >>= 1
    end
    x
end
```

Après un appel comme `x = 5; y = power_by_squaring(x, 4)`, vous obtiendriez le résultat attendu : `x == 5 && y == 625`. Cependant, supposons maintenant que `*=`, lorsqu'il est utilisé avec des matrices, modifie le côté gauche. Il y aurait deux problèmes :

  * Pour les matrices carrées générales, `A = A*B` ne peut pas être implémenté sans stockage temporaire : `A[1,1]` est calculé et stocké sur le côté gauche avant que vous ayez fini de l'utiliser sur le côté droit.
  * Supposons que vous soyez prêt à allouer un temporaire pour le calcul (ce qui éliminerait la plupart des raisons de faire fonctionner `*=` en place) ; si vous tiriez parti de la mutabilité de `x`, alors cette fonction se comporterait différemment pour des entrées mutables et immuables. En particulier, pour un `x` immuable, après l'appel, vous auriez (en général) `y != x`, mais pour un `x` mutable, vous auriez `y == x`.

Parce que le soutien à la programmation générique est jugé plus important que les optimisations de performance potentielles qui peuvent être réalisées par d'autres moyens (par exemple, en utilisant le broadcasting ou des boucles explicites), des opérateurs comme `+=` et `*=` fonctionnent en réaffectant de nouvelles valeurs.

## [Asynchronous IO and concurrent synchronous writes](@id faq-async-io)

### Why do concurrent writes to the same stream result in inter-mixed output?

Bien que l'API de streaming I/O soit synchrone, l'implémentation sous-jacente est entièrement asynchrone.

Veuillez fournir le contenu Markdown que vous souhaitez traduire en français.

```jldoctest
julia> @sync for i in 1:3
           @async write(stdout, string(i), " Foo ", " Bar ")
       end
123 Foo  Foo  Foo  Bar  Bar  Bar
```

Cela se produit parce que, bien que l'appel `write` soit synchrone, l'écriture de chaque argument cède à d'autres tâches en attendant que cette partie de l'I/O soit terminée.

`print` et `println` "verrouillent" le flux pendant un appel. Par conséquent, changer `write` en `println` dans l'exemple ci-dessus donne :

```jldoctest
julia> @sync for i in 1:3
           @async println(stdout, string(i), " Foo ", " Bar ")
       end
1 Foo  Bar
2 Foo  Bar
3 Foo  Bar
```

Vous pouvez verrouiller vos écritures avec un `ReentrantLock` comme ceci :

```jldoctest
julia> l = ReentrantLock();

julia> @sync for i in 1:3
           @async begin
               lock(l)
               try
                   write(stdout, string(i), " Foo ", " Bar ")
               finally
                   unlock(l)
               end
           end
       end
1 Foo  Bar 2 Foo  Bar 3 Foo  Bar
```

## Arrays

### [What are the differences between zero-dimensional arrays and scalars?](@id faq-array-0dim)

Les tableaux à zéro dimension sont des tableaux de la forme `Array{T,0}`. Ils se comportent de manière similaire aux scalaires, mais il existe des différences importantes. Ils méritent une mention spéciale car ils constituent un cas particulier qui a un sens logique compte tenu de la définition générique des tableaux, mais qui peut sembler un peu contre-intuitif au début. La ligne suivante définit un tableau à zéro dimension :

```
julia> A = zeros()
0-dimensional Array{Float64,0}:
0.0
```

Dans cet exemple, `A` est un conteneur mutable qui contient un élément, qui peut être défini par `A[] = 1.0` et récupéré avec `A[]`. Tous les tableaux à zéro dimension ont la même taille (`size(A) == ()`) et la même longueur (`length(A) == 1`). En particulier, les tableaux à zéro dimension ne sont pas vides. Si cela vous semble contre-intuitif, voici quelques idées qui pourraient aider à comprendre la définition de Julia.

  * Les tableaux à zéro dimension sont le "point" par rapport à la "ligne" du vecteur et au "plan" de la matrice. Tout comme une ligne n'a pas de surface (mais représente tout de même un ensemble de choses), un point n'a pas de longueur ni aucune dimension (mais représente tout de même une chose).
  * Nous définissons `prod(())` comme étant 1, et le nombre total d'éléments dans un tableau est le produit de la taille. La taille d'un tableau à zéro dimension est `()`, et par conséquent, sa longueur est `1`.
  * Les tableaux à zéro dimension n'ont pas de dimensions dans lesquelles vous pouvez indexer – ils sont juste `A[]`. Nous pouvons appliquer la même règle du "dernier un" pour eux que pour toutes les autres dimensions de tableau, donc vous pouvez effectivement les indexer comme `A[1]`, `A[1,1]`, etc ; voir [Omitted and extra indices](@ref).

Il est également important de comprendre les différences par rapport aux scalaires ordinaires. Les scalaires ne sont pas des conteneurs mutables (même s'ils sont itérables et définissent des choses comme `length`, `getindex`, *par exemple* `1[] == 1`). En particulier, si `x = 0.0` est défini comme un scalaire, il est erroné d'essayer de changer sa valeur via `x[] = 1.0`. Un scalaire `x` peut être converti en un tableau à zéro dimension qui le contient via `fill(x)`, et inversement, un tableau à zéro dimension `a` peut être converti en le scalaire contenu via `a[]`. Une autre différence est qu'un scalaire peut participer à des opérations d'algèbre linéaire telles que `2 * rand(2,2)`, mais l'opération analogue avec un tableau à zéro dimension `fill(2) * rand(2,2)` est une erreur.

### Why are my Julia benchmarks for linear algebra operations different from other languages?

Vous pouvez constater que des benchmarks simples des éléments de base de l'algèbre linéaire comme

```julia
using BenchmarkTools
A = randn(1000, 1000)
B = randn(1000, 1000)
@btime $A \ $B
@btime $A * $B
```

peut être différent par rapport à d'autres langages comme Matlab ou R.

Puisque des opérations comme celle-ci sont de très fines enveloppes autour des fonctions BLAS pertinentes, la raison de la divergence est très probablement liée à

1. la bibliothèque BLAS que chaque langage utilise,
2. le nombre de threads concurrents.

Julia compile et utilise sa propre copie d'OpenBLAS, avec un nombre de threads actuellement limité à `8` (ou au nombre de vos cœurs).

Modifier les paramètres d'OpenBLAS ou compiler Julia avec une autre bibliothèque BLAS, par exemple [Intel MKL](https://software.intel.com/en-us/mkl), peut offrir des améliorations de performance. Vous pouvez utiliser [MKL.jl](https://github.com/JuliaComputing/MKL.jl), un package qui permet à l'algèbre linéaire de Julia d'utiliser Intel MKL BLAS et LAPACK au lieu d'OpenBLAS, ou rechercher dans le forum de discussion des suggestions sur la façon de configurer cela manuellement. Notez qu'Intel MKL ne peut pas être inclus avec Julia, car il n'est pas open source.

## Computing cluster

### How do I manage precompilation caches in distributed file systems?

Lors de l'utilisation de Julia dans des installations de calcul haute performance (HPC) avec des systèmes de fichiers partagés, il est recommandé d'utiliser un dépôt partagé (via la variable d'environnement [`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH)). Depuis Julia v1.10, plusieurs processus Julia sur des travailleurs fonctionnellement similaires et utilisant le même dépôt se coordonneront via des verrous de fichier pidfile pour ne dépenser des efforts de précompilation que sur un processus pendant que les autres attendent. Le processus de précompilation indiquera quand le processus est en train de précompiler ou d'attendre un autre qui est en train de précompiler. Si non interactif, les messages sont via `@debug`.

Cependant, en raison de la mise en cache du code binaire, le rejet du cache depuis la version 1.9 est plus strict et les utilisateurs peuvent avoir besoin de définir la variable d'environnement [`JULIA_CPU_TARGET`](@ref JULIA_CPU_TARGET) de manière appropriée pour obtenir un cache unique utilisable dans tout l'environnement HPC.

## Julia Releases

### Do I want to use the Stable, LTS, or nightly version of Julia?

La version Stable de Julia est la dernière version publiée de Julia, c'est la version que la plupart des gens voudront exécuter. Elle dispose des dernières fonctionnalités, y compris des performances améliorées. La version Stable de Julia est versionnée selon [SemVer](https://semver.org/) sous la forme v1.x.y. Une nouvelle version mineure de Julia correspondant à une nouvelle version Stable est publiée environ tous les 4-5 mois après quelques semaines de tests en tant que candidat à la publication. Contrairement à la version LTS, la version Stable ne recevra normalement pas de corrections de bogues après qu'une autre version Stable de Julia a été publiée. Cependant, la mise à niveau vers la prochaine version Stable sera toujours possible, car chaque version de Julia v1.x continuera à exécuter du code écrit pour des versions antérieures.

Vous pouvez préférer la version LTS (Long Term Support) de Julia si vous recherchez une base de code très stable. La version LTS actuelle de Julia est versionnée selon SemVer en tant que v1.6.x ; cette branche continuera de recevoir des corrections de bogues jusqu'à ce qu'une nouvelle branche LTS soit choisie, moment auquel la série v1.6.x ne recevra plus de corrections de bogues régulières et tous les utilisateurs sauf les plus conservateurs seront conseillés de passer à la nouvelle série de versions LTS. En tant que développeur de package, vous pouvez préférer développer pour la version LTS, afin de maximiser le nombre d'utilisateurs qui peuvent utiliser votre package. Selon SemVer, le code écrit pour v1.0 continuera de fonctionner pour toutes les futures versions LTS et Stables. En général, même en visant la LTS, on peut développer et exécuter du code dans la dernière version Stable, pour profiter des performances améliorées ; tant que l'on évite d'utiliser de nouvelles fonctionnalités (comme des fonctions de bibliothèque ajoutées ou de nouvelles méthodes).

Vous pouvez préférer la version nocturne de Julia si vous souhaitez profiter des dernières mises à jour du langage et que cela ne vous dérange pas si la version disponible aujourd'hui ne fonctionne pas toujours. Comme son nom l'indique, des versions de la version nocturne sont publiées environ chaque nuit (en fonction de la stabilité de l'infrastructure de construction). En général, les versions nocturnes publiées sont assez sûres à utiliser : votre code ne prendra pas feu. Cependant, il peut y avoir des régressions occasionnelles et/ou des problèmes qui ne seront pas découverts avant des tests préliminaires plus approfondis. Vous souhaiterez peut-être tester contre la version nocturne pour vous assurer que de telles régressions qui affectent votre cas d'utilisation sont détectées avant qu'une version ne soit publiée.

Enfin, vous pouvez également envisager de compiler Julia à partir des sources pour vous-même. Cette option est principalement destinée aux personnes qui se sentent à l'aise avec la ligne de commande, ou qui souhaitent apprendre. Si cela vous décrit, vous pourriez également être intéressé par la lecture de notre [guidelines for contributing](https://github.com/JuliaLang/julia/blob/master/CONTRIBUTING.md).

Les liens vers chacun de ces types de téléchargement peuvent être trouvés sur la page de téléchargement à [https://julialang.org/downloads/](https://julialang.org/downloads/). Notez que toutes les versions de Julia ne sont pas disponibles pour toutes les plateformes.

### How can I transfer the list of installed packages after updating my version of Julia?

Chaque version mineure de Julia a son propre [environment](https://docs.julialang.org/en/v1/manual/code-loading/#Environments-1) par défaut. En conséquence, lors de l'installation d'une nouvelle version mineure de Julia, les packages que vous avez ajoutés avec la version mineure précédente ne seront pas disponibles par défaut. L'environnement pour une version donnée de Julia est défini par les fichiers `Project.toml` et `Manifest.toml` dans un dossier correspondant au numéro de version dans `.julia/environments/`, par exemple, `.julia/environments/v1.3`.

Si vous installez une nouvelle version mineure de Julia, disons `1.4`, et que vous souhaitez utiliser dans son environnement par défaut les mêmes packages que dans une version précédente (par exemple `1.3`), vous pouvez copier le contenu du fichier `Project.toml` du dossier `1.3` vers `1.4`. Ensuite, dans une session de la nouvelle version de Julia, entrez le "mode de gestion des packages" en tapant la touche `]`, et exécutez la commande [`instantiate`](https://julialang.github.io/Pkg.jl/v1/api/#Pkg.instantiate).

Cette opération résoudra un ensemble de paquets réalisables à partir du fichier copié qui sont compatibles avec la version cible de Julia, et les installera ou les mettra à jour si cela est approprié. Si vous souhaitez reproduire non seulement l'ensemble des paquets, mais aussi les versions que vous utilisiez dans la version précédente de Julia, vous devez également copier le fichier `Manifest.toml` avant d'exécuter la commande Pkg `instantiate`. Cependant, notez que les paquets peuvent définir des contraintes de compatibilité qui peuvent être affectées par le changement de version de Julia, donc l'ensemble exact des versions que vous aviez dans `1.3` peut ne pas fonctionner pour `1.4`.
