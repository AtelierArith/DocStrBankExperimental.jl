# [Functions](@id man-functions)

En Julia, une fonction est un objet qui associe un tuple de valeurs d'argument à une valeur de retour. Les fonctions Julia ne sont pas des fonctions mathématiques pures, car elles peuvent modifier et être affectées par l'état global du programme. La syntaxe de base pour définir des fonctions en Julia est :

```jldoctest
julia> function f(x, y)
           x + y
       end
f (generic function with 1 method)
```

Cette fonction accepte deux arguments `x` et `y` et renvoie la valeur de la dernière expression évaluée, qui est `x + y`.

Il existe une seconde syntaxe plus concise pour définir une fonction en Julia. La syntaxe traditionnelle de déclaration de fonction démontrée ci-dessus est équivalente à la suivante "forme d'assignation" compacte :

```jldoctest fofxy
julia> f(x, y) = x + y
f (generic function with 1 method)
```

Dans le formulaire d'affectation, le corps de la fonction doit être une seule expression, bien qu'il puisse s'agir d'une expression composée (voir [Compound Expressions](@ref man-compound-expressions)). Les définitions de fonctions courtes et simples sont courantes en Julia. La syntaxe de fonction courte est donc assez idiomatique, réduisant considérablement à la fois la saisie et le bruit visuel.

Une fonction est appelée en utilisant la syntaxe traditionnelle des parenthèses :

```jldoctest fofxy
julia> f(2, 3)
5
```

Sans parenthèses, l'expression `f` fait référence à l'objet fonction, et peut être passé comme n'importe quelle autre valeur :

```jldoctest fofxy
julia> g = f;

julia> g(2, 3)
5
```

Comme pour les variables, Unicode peut également être utilisé pour les noms de fonctions :

```jldoctest
julia> ∑(x, y) = x + y
∑ (generic function with 1 method)

julia> ∑(2, 3)
5
```

## [Argument Passing Behavior](@id man-argument-passing)

Les arguments de fonction en Julia suivent une convention parfois appelée "passage par partage", ce qui signifie que les valeurs ne sont pas copiées lorsqu'elles sont passées aux fonctions. Les arguments de fonction eux-mêmes agissent comme de nouvelles *liaisons* de variables (de nouveaux "noms" qui peuvent faire référence à des valeurs), tout comme [assignments](@ref man-assignment-expressions) `argument_name = argument_value`, de sorte que les objets auxquels ils font référence sont identiques aux valeurs passées. Les modifications apportées à des valeurs mutables (telles que les `Array`s) effectuées dans une fonction seront visibles par l'appelant. (C'est le même comportement que l'on trouve dans Scheme, la plupart des Lisps, Python, Ruby et Perl, parmi d'autres langages dynamiques.)

Par exemple, dans la fonction

```julia
function f(x, y)
    x[1] = 42    # mutates x
    y = 7 + y    # new binding for y, no mutation
    return y
end
```

L'instruction `x[1] = 42` *mutate* l'objet `x`, et donc ce changement *sera* visible dans le tableau passé par l'appelant pour cet argument. D'autre part, l'assignation `y = 7 + y` change la *liaison* ("nom") `y` pour faire référence à une nouvelle valeur `7 + y`, plutôt que de muter l'objet *original* référencé par `y`, et donc ne *change pas* l'argument correspondant passé par l'appelant. Cela peut être vu si nous appelons `f(x, y)` :

```julia-repl
julia> a = [4, 5, 6]
3-element Vector{Int64}:
 4
 5
 6

julia> b = 3
3

julia> f(a, b) # returns 7 + b == 10
10

julia> a  # a[1] is changed to 42 by f
3-element Vector{Int64}:
 42
  5
  6

julia> b  # not changed
3
```

En tant que convention courante en Julia (pas une exigence syntaxique), une telle fonction serait [typically be named `f!(x, y)`](@ref man-punctuation) plutôt que `f(x, y)`, comme un rappel visuel au site d'appel que l'au moins un des arguments (souvent le premier) est en cours de mutation.

!!! warning "Shared memory between arguments"
    Le comportement d'une fonction mutante peut être inattendu lorsqu'un argument muté partage de la mémoire avec un autre argument, une situation connue sous le nom d'aliasing (par exemple, lorsque l'un est une vue de l'autre). À moins que la docstring de la fonction n'indique explicitement que l'aliasing produit le résultat attendu, il incombe à l'appelant de garantir un comportement approprié sur de telles entrées.


## Argument-type declarations

Vous pouvez déclarer les types des arguments de fonction en ajoutant `::TypeName` au nom de l'argument, comme d'habitude pour [Type Declarations](@ref) en Julia. Par exemple, la fonction suivante calcule [Fibonacci numbers](https://en.wikipedia.org/wiki/Fibonacci_number) de manière récursive :

```
fib(n::Integer) = n ≤ 2 ? one(n) : fib(n-1) + fib(n-2)
```

et la spécification `::Integer` signifie qu'elle ne sera appelable que lorsque `n` est un sous-type du type [abstract](@ref man-abstract-types) `Integer`.

Les déclarations de types d'arguments **n'ont normalement aucun impact sur les performances** : peu importe quels types d'arguments (le cas échéant) sont déclarés, Julia compile une version spécialisée de la fonction pour les types d'arguments réels passés par l'appelant. Par exemple, appeler `fib(1)` déclenchera la compilation d'une version spécialisée de `fib` optimisée spécifiquement pour les arguments `Int`, qui sera ensuite réutilisée si `fib(7)` ou `fib(15)` sont appelés. (Il existe des exceptions rares où une déclaration de type d'argument peut déclencher des spécialisations supplémentaires du compilateur ; voir : [Be aware of when Julia avoids specializing](@ref).) Les raisons les plus courantes de déclarer des types d'arguments en Julia sont, à la place :

  * **Dispatch :** Comme expliqué dans [Methods](@ref), vous pouvez avoir différentes versions ("méthodes") d'une fonction pour différents types d'arguments, auquel cas les types d'arguments sont utilisés pour déterminer quelle implémentation est appelée pour quels arguments. Par exemple, vous pourriez implémenter un algorithme complètement différent `fib(x::Number) = ...` qui fonctionne pour tout type `Number` en utilisant [Binet's formula](https://en.wikipedia.org/wiki/Fibonacci_number#Binet%27s_formula) pour l'étendre à des valeurs non entières.
  * **Exactitude :** Les déclarations de type peuvent être utiles si votre fonction ne renvoie des résultats corrects que pour certains types d'arguments. Par exemple, si nous omettions les types d'arguments et écrivions `fib(n) = n ≤ 2 ? one(n) : fib(n-1) + fib(n-2)`, alors `fib(1.5)` nous donnerait silencieusement la réponse absurde `1.0`.
  * **Clarté :** Les déclarations de type peuvent servir de forme de documentation sur les arguments attendus.

Cependant, c'est une **erreur courante de restreindre excessivement les types d'arguments**, ce qui peut limiter inutilement l'applicabilité de la fonction et empêcher son réemploi dans des circonstances que vous n'aviez pas anticipées. Par exemple, la fonction `fib(n::Integer)` ci-dessus fonctionne également bien pour les arguments `Int` (entiers machine) et `BigInt` (entiers à précision arbitraire) (voir [BigFloats and BigInts](@ref BigFloats-and-BigInts)), ce qui est particulièrement utile car les nombres de Fibonacci croissent de manière exponentielle rapide et dépasseront rapidement tout type à précision fixe comme `Int` (voir [Overflow behavior](@ref)). Si nous avions déclaré notre fonction comme `fib(n::Int)`, cependant, l'application à `BigInt` aurait été empêchée sans raison. En général, vous devriez utiliser les types abstraits les plus généraux applicables pour les arguments, et **en cas de doute, omettez les types d'arguments**. Vous pouvez toujours ajouter des spécifications de type d'argument plus tard si elles deviennent nécessaires, et vous ne sacrifiez ni performance ni fonctionnalité en les omettant.

## The `return` Keyword

La valeur renvoyée par une fonction est la valeur de la dernière expression évaluée, qui, par défaut, est la dernière expression dans le corps de la définition de la fonction. Dans la fonction d'exemple, `f`, de la section précédente, c'est la valeur de l'expression `x + y`. En alternative, comme dans de nombreux autres langages, le mot-clé `return` permet à une fonction de renvoyer immédiatement, en fournissant une expression dont la valeur est renvoyée :

```julia
function g(x, y)
    return x * y
    x + y
end
```

Puisque les définitions de fonction peuvent être saisies dans des sessions interactives, il est facile de comparer ces définitions :

```jldoctest
julia> f(x, y) = x + y
f (generic function with 1 method)

julia> function g(x, y)
           return x * y
           x + y
       end
g (generic function with 1 method)

julia> f(2, 3)
5

julia> g(2, 3)
6
```

Bien sûr, dans un corps de fonction purement linéaire comme `g`, l'utilisation de `return` est inutile puisque l'expression `x + y` n'est jamais évaluée et nous pourrions simplement faire de `x * y` la dernière expression de la fonction et omettre le `return`. En conjonction avec d'autres flux de contrôle, cependant, `return` est réellement utile. Voici, par exemple, une fonction qui calcule la longueur de l'hypoténuse d'un triangle rectangle avec des côtés de longueur `x` et `y`, évitant le débordement :

```jldoctest
julia> function hypot(x, y)
           x = abs(x)
           y = abs(y)
           if x > y
               r = y/x
               return x*sqrt(1 + r*r)
           end
           if y == 0
               return zero(x)
           end
           r = x/y
           return y*sqrt(1 + r*r)
       end
hypot (generic function with 1 method)

julia> hypot(3, 4)
5.0
```

Il y a trois points de retour possibles de cette fonction, retournant les valeurs de trois expressions différentes, en fonction des valeurs de `x` et `y`. Le `return` sur la dernière ligne pourrait être omis puisqu'il s'agit de la dernière expression.

### [Return type](@id man-functions-return-type)

Un type de retour peut être spécifié dans la déclaration de la fonction en utilisant l'opérateur `::`. Cela convertit la valeur de retour au type spécifié.

```jldoctest
julia> function g(x, y)::Int8
           return x * y
       end;

julia> typeof(g(1, 2))
Int8
```

Cette fonction renverra toujours un `Int8` indépendamment des types de `x` et `y`. Voir [Type Declarations](@ref) pour plus d'informations sur les types de retour.

Les déclarations de type de retour sont **rarement utilisées** en Julia : en général, vous devriez plutôt écrire des fonctions "stables en type" dans lesquelles le compilateur de Julia peut automatiquement inférer le type de retour. Pour plus d'informations, consultez le chapitre [Performance Tips](@ref man-performance-tips).

### Returning nothing

Pour les fonctions qui n'ont pas besoin de retourner une valeur (fonctions utilisées uniquement pour certains effets secondaires), la convention Julia est de retourner la valeur [`nothing`](@ref) :

```julia
function printx(x)
    println("x = $x")
    return nothing
end
```

C'est une *convention* dans le sens où `nothing` n'est pas un mot-clé Julia mais seulement un objet singleton de type `Nothing`. De plus, vous remarquerez peut-être que l'exemple de fonction `printx` ci-dessus est artificiel, car `println` renvoie déjà `nothing`, de sorte que la ligne `return` est redondante.

Il existe deux formes abrégées possibles pour l'expression `return nothing`. D'une part, le mot-clé `return` renvoie implicitement `nothing`, il peut donc être utilisé seul. D'autre part, puisque les fonctions renvoient implicitement leur dernière expression évaluée, `nothing` peut être utilisé seul lorsqu'il s'agit de la dernière expression. La préférence pour l'expression `return nothing` par rapport à `return` ou `nothing` seul est une question de style de codage.

## Operators Are Functions

En Julia, la plupart des opérateurs ne sont que des fonctions avec un support pour une syntaxe spéciale. (Les exceptions sont les opérateurs avec des sémantiques d'évaluation spéciales comme `&&` et `||`. Ces opérateurs ne peuvent pas être des fonctions puisque [Short-Circuit Evaluation](@ref) exige que leurs opérandes ne soient pas évalués avant l'évaluation de l'opérateur.) En conséquence, vous pouvez également les appliquer en utilisant des listes d'arguments entre parenthèses, tout comme vous le feriez pour n'importe quelle autre fonction :

```jldoctest
julia> 1 + 2 + 3
6

julia> +(1, 2, 3)
6
```

La forme infixe est exactement équivalente à la forme d'application de fonction – en fait, la première est analysée pour produire l'appel de fonction en interne. Cela signifie également que vous pouvez assigner et passer des opérateurs tels que [`+`](@ref) et [`*`](@ref) tout comme vous le feriez avec d'autres valeurs de fonction :

```jldoctest
julia> f = +;

julia> f(1, 2, 3)
6
```

Sous le nom `f`, la fonction ne prend pas en charge la notation infixe, cependant.

## Operators With Special Names

Quelques expressions spéciales correspondent à des appels de fonctions avec des noms non évidents. Celles-ci sont :

| Expression            | Calls                                    |
|:--------------------- |:---------------------------------------- |
| `[A B C ...]`         | [`hcat`](@ref)                           |
| `[A; B; C; ...]`      | [`vcat`](@ref)                           |
| `[A B; C D; ...]`     | [`hvcat`](@ref)                          |
| `[A; B;; C; D;; ...]` | [`hvncat`](@ref)                         |
| `A'`                  | [`adjoint`](@ref)                        |
| `A[i]`                | [`getindex`](@ref)                       |
| `A[i] = x`            | [`setindex!`](@ref)                      |
| `A.n`                 | [`getproperty`](@ref Base.getproperty)   |
| `A.n = x`             | [`setproperty!`](@ref Base.setproperty!) |

Notez que des expressions similaires à `[A; B;; C; D;; ...]`, mais avec plus de deux `;` consécutifs, correspondent également à des appels à `hvncat`.

## [Anonymous Functions](@id man-anonymous-functions)

Les fonctions en Julia sont [first-class objects](https://en.wikipedia.org/wiki/First-class_citizen) : elles peuvent être assignées à des variables et appelées en utilisant la syntaxe d'appel de fonction standard à partir de la variable à laquelle elles ont été assignées. Elles peuvent être utilisées comme arguments et peuvent être retournées comme valeurs. Elles peuvent également être créées de manière anonyme, sans leur donner de nom, en utilisant l'une de ces syntaxes :

```jldoctest
julia> x -> x^2 + 2x - 1
#1 (generic function with 1 method)

julia> function (x)
           x^2 + 2x - 1
       end
#3 (generic function with 1 method)
```

Chaque déclaration crée une fonction prenant un argument `x` et retournant la valeur du polynôme `x^2 + 2x - 1` à cette valeur. Remarquez que le résultat est une fonction générique, mais avec un nom généré par le compilateur basé sur une numérotation consécutive.

L'utilisation principale des fonctions anonymes est de les passer à des fonctions qui prennent d'autres fonctions comme arguments. Un exemple classique est [`map`](@ref), qui applique une fonction à chaque valeur d'un tableau et renvoie un nouveau tableau contenant les valeurs résultantes :

```jldoctest
julia> map(round, [1.2, 3.5, 1.7])
3-element Vector{Float64}:
 1.0
 4.0
 2.0
```

C'est bien si une fonction nommée effectuant la transformation existe déjà à passer comme premier argument à [`map`](@ref). Souvent, cependant, une fonction nommée prête à l'emploi n'existe pas. Dans ces situations, la construction de fonction anonyme permet de créer facilement un objet fonction à usage unique sans avoir besoin d'un nom :

```jldoctest
julia> map(x -> x^2 + 2x - 1, [1, 3, -1])
3-element Vector{Int64}:
  2
 14
 -2
```

Une fonction anonyme acceptant plusieurs arguments peut être écrite en utilisant la syntaxe `(x,y,z)->2x+y-z`.

Les déclarations de type d'argument pour les fonctions anonymes fonctionnent comme pour les fonctions nommées, par exemple `x::Integer->2x`. Le type de retour d'une fonction anonyme ne peut pas être spécifié.

Une fonction anonyme sans argument peut être écrite comme `()->2+2`. L'idée d'une fonction sans arguments peut sembler étrange, mais elle est utile dans les cas où un résultat ne peut pas (ou ne doit pas) être pré-calculé. Par exemple, Julia a une fonction sans argument [`time`](@ref) qui renvoie l'heure actuelle en secondes, et donc `seconds = ()->round(Int, time())` est une fonction anonyme qui renvoie cette heure arrondie à l'entier le plus proche assigné à la variable `seconds`. Chaque fois que cette fonction anonyme est appelée comme `seconds()`, l'heure actuelle sera calculée et renvoyée.

## Tuples

Julia a une structure de données intégrée appelée *tuple* qui est étroitement liée aux arguments de fonction et aux valeurs de retour. Un tuple est un conteneur de longueur fixe qui peut contenir n'importe quelles valeurs, mais ne peut pas être modifié (il est *immuable*). Les tuples sont construits avec des virgules et des parenthèses, et peuvent être accédés par indexation :

```jldoctest
julia> (1, 1+1)
(1, 2)

julia> (1,)
(1,)

julia> x = (0.0, "hello", 6*7)
(0.0, "hello", 42)

julia> x[2]
"hello"
```

Remarquez qu'un tuple de longueur 1 doit être écrit avec une virgule, `(1,)`, car `(1)` ne serait qu'une valeur entre parenthèses. `()` représente le tuple vide (de longueur 0).

## Named Tuples

Les composants des tuples peuvent être nommés de manière optionnelle, auquel cas un *tuple nommé* est construit :

```jldoctest
julia> x = (a=2, b=1+2)
(a = 2, b = 3)

julia> x[1]
2

julia> x.a
2
```

Les champs des tuples nommés peuvent être accédés par nom en utilisant la syntaxe par point (`x.a`) en plus de la syntaxe d'indexation régulière (`x[1]` ou `x[:a]`).

## [Destructuring Assignment and Multiple Return Values](@id destructuring-assignment)

Une liste de variables séparées par des virgules (éventuellement entourée de parenthèses) peut apparaître sur le côté gauche d'une affectation : la valeur sur le côté droit est *déstructurée* en itérant et en assignant à chaque variable à tour de rôle :

```jldoctest
julia> (a, b, c) = 1:3
1:3

julia> b
2
```

La valeur à droite doit être un itérateur (voir [Iteration interface](@ref man-interface-iteration)) d'au moins la même longueur que le nombre de variables à gauche (tout élément excédentaire de l'itérateur est ignoré).

Cela peut être utilisé pour renvoyer plusieurs valeurs à partir de fonctions en renvoyant un tuple ou une autre valeur itérable. Par exemple, la fonction suivante renvoie deux valeurs :

```jldoctest foofunc
julia> function foo(a, b)
           a+b, a*b
       end
foo (generic function with 1 method)
```

Si vous l'appelez dans une session interactive sans assigner la valeur de retour nulle part, vous verrez le tuple retourné :

```jldoctest foofunc
julia> foo(2, 3)
(5, 6)
```

L'affectation par décomposition extrait chaque valeur dans une variable :

```jldoctest foofunc
julia> x, y = foo(2, 3)
(5, 6)

julia> x
5

julia> y
6
```

Une autre utilisation courante est l'échange de variables :

```jldoctest foofunc
julia> y, x = x, y
(5, 6)

julia> x
6

julia> y
5
```

Si seulement un sous-ensemble des éléments de l'itérateur est requis, une convention courante consiste à assigner les éléments ignorés à une variable composée uniquement de traits de soulignement `_` (qui est un nom de variable autrement invalide, voir [Allowed Variable Names](@ref man-allowed-variable-names)):

```jldoctest
julia> _, _, _, d = 1:10
1:10

julia> d
4
```

D'autres expressions valides du côté gauche peuvent être utilisées comme éléments de la liste d'affectation, ce qui appellera [`setindex!`](@ref) ou [`setproperty!`](@ref), ou déstructurer récursivement des éléments individuels de l'itérateur :

```jldoctest
julia> X = zeros(3);

julia> X[1], (a, b) = (1, (2, 3))
(1, (2, 3))

julia> X
3-element Vector{Float64}:
 1.0
 0.0
 0.0

julia> a
2

julia> b
3
```

!!! compat "Julia 1.6"
    `...` avec l'assignation nécessite Julia 1.6


Si le dernier symbole de la liste d'affectation est suffixé par `...` (appelé *slurping*), alors il sera assigné une collection ou un itérateur paresseux des éléments restants de l'itérateur du côté droit :

```jldoctest
julia> a, b... = "hello"
"hello"

julia> a
'h': ASCII/Unicode U+0068 (category Ll: Letter, lowercase)

julia> b
"ello"

julia> a, b... = Iterators.map(abs2, 1:4)
Base.Generator{UnitRange{Int64}, typeof(abs2)}(abs2, 1:4)

julia> a
1

julia> b
Base.Iterators.Rest{Base.Generator{UnitRange{Int64}, typeof(abs2)}, Int64}(Base.Generator{UnitRange{Int64}, typeof(abs2)}(abs2, 1:4), 1)
```

Voir [`Base.rest`](@ref) pour des détails sur la gestion précise et la personnalisation des itérateurs spécifiques.

!!! compat "Julia 1.9"
    `...` dans une position non finale d'une affectation nécessite Julia 1.9


Le slurping dans les affectations peut également se produire dans n'importe quelle autre position. Contrairement au slurping de la fin d'une collection, cependant, cela sera toujours avide.

```jldoctest
julia> a, b..., c = 1:5
1:5

julia> a
1

julia> b
3-element Vector{Int64}:
 2
 3
 4

julia> c
5

julia> front..., tail = "Hi!"
"Hi!"

julia> front
"Hi"

julia> tail
'!': ASCII/Unicode U+0021 (category Po: Punctuation, other)
```

Ceci est implémenté en termes de la fonction [`Base.split_rest`](@ref).

Notez que pour les définitions de fonctions variadiques, le slurping n'est autorisé qu'en position finale. Cela ne s'applique pas à [single argument destructuring](@ref man-argument-destructuring), car cela n'affecte pas l'appel de méthode :

```jldoctest
julia> f(x..., y) = x
ERROR: syntax: invalid "..." on non-final argument
Stacktrace:
[...]

julia> f((x..., y)) = x
f (generic function with 1 method)

julia> f((1, 2, 3))
(1, 2)
```

## Property destructuring

Au lieu de déstructurer en fonction de l'itération, le côté droit des affectations peut également être déstructuré en utilisant des noms de propriétés. Cela suit la syntaxe des NamedTuples et fonctionne en assignant à chaque variable à gauche une propriété du côté droit de l'affectation ayant le même nom en utilisant `getproperty` :

```jldoctest
julia> (; b, a) = (a=1, b=2, c=3)
(a = 1, b = 2, c = 3)

julia> a
1

julia> b
2
```

## [Argument destructuring](@id man-argument-destructuring)

La fonctionnalité de déstructuration peut également être utilisée dans un argument de fonction. Si le nom d'un argument de fonction est écrit sous forme de tuple (par exemple, `(x, y)`) au lieu d'un simple symbole, alors une assignation `(x, y) = argument` sera insérée pour vous :

```julia-repl
julia> minmax(x, y) = (y < x) ? (y, x) : (x, y)

julia> gap((min, max)) = max - min

julia> gap(minmax(10, 2))
8
```

Remarquez l'ensemble supplémentaire de parenthèses dans la définition de `gap`. Sans celles-ci, `gap` serait une fonction à deux arguments, et cet exemple ne fonctionnerait pas.

De la même manière, la déstructuration d'objet peut également être utilisée pour les arguments de fonction :

```julia-repl
julia> foo((; x, y)) = x + y
foo (generic function with 1 method)

julia> foo((x=1, y=2))
3

julia> struct A
           x
           y
       end

julia> foo(A(3, 4))
7
```

Pour les fonctions anonymes, la déstructuration d'un seul argument nécessite une virgule supplémentaire :

```
julia> map(((x, y),) -> x + y, [(1, 2), (3, 4)])
2-element Array{Int64,1}:
 3
 7
```

## Varargs Functions

Il est souvent pratique de pouvoir écrire des fonctions prenant un nombre arbitraire d'arguments. De telles fonctions sont traditionnellement connues sous le nom de fonctions "varargs", qui est l'abréviation de "nombre variable d'arguments". Vous pouvez définir une fonction varargs en suivant le dernier argument positionnel d'une ellipse :

```jldoctest barfunc
julia> bar(a, b, x...) = (a, b, x)
bar (generic function with 1 method)
```

Les variables `a` et `b` sont liées aux deux premières valeurs d'argument comme d'habitude, et la variable `x` est liée à une collection itérable des zéro ou plusieurs valeurs passées à `bar` après ses deux premiers arguments :

```jldoctest barfunc
julia> bar(1, 2)
(1, 2, ())

julia> bar(1, 2, 3)
(1, 2, (3,))

julia> bar(1, 2, 3, 4)
(1, 2, (3, 4))

julia> bar(1, 2, 3, 4, 5, 6)
(1, 2, (3, 4, 5, 6))
```

Dans tous ces cas, `x` est lié à un tuple des valeurs finales passées à `bar`.

Il est possible de contraindre le nombre de valeurs passées en tant qu'argument variable ; cela sera discuté plus tard dans [Parametrically-constrained Varargs methods](@ref).

D'un autre côté, il est souvent pratique de "décomposer" les valeurs contenues dans une collection itérable dans un appel de fonction en tant qu'arguments individuels. Pour ce faire, on utilise également `...` mais dans l'appel de fonction à la place :

```jldoctest barfunc
julia> x = (3, 4)
(3, 4)

julia> bar(1, 2, x...)
(1, 2, (3, 4))
```

Dans ce cas, un tuple de valeurs est inséré dans un appel varargs précisément là où le nombre variable d'arguments est requis. Ce n'est cependant pas nécessaire :

```jldoctest barfunc
julia> x = (2, 3, 4)
(2, 3, 4)

julia> bar(1, x...)
(1, 2, (3, 4))

julia> x = (1, 2, 3, 4)
(1, 2, 3, 4)

julia> bar(x...)
(1, 2, (3, 4))
```

De plus, l'objet itérable éclaté dans un appel de fonction n'a pas besoin d'être un tuple :

```jldoctest barfunc
julia> x = [3, 4]
2-element Vector{Int64}:
 3
 4

julia> bar(1, 2, x...)
(1, 2, (3, 4))

julia> x = [1, 2, 3, 4]
4-element Vector{Int64}:
 1
 2
 3
 4

julia> bar(x...)
(1, 2, (3, 4))
```

Aussi, la fonction dans laquelle les arguments sont étalés n'a pas besoin d'être une fonction varargs (bien qu'elle le soit souvent) :

```jldoctest
julia> baz(a, b) = a + b;

julia> args = [1, 2]
2-element Vector{Int64}:
 1
 2

julia> baz(args...)
3

julia> args = [1, 2, 3]
3-element Vector{Int64}:
 1
 2
 3

julia> baz(args...)
ERROR: MethodError: no method matching baz(::Int64, ::Int64, ::Int64)
The function `baz` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  baz(::Any, ::Any)
   @ Main none:1

Stacktrace:
[...]
```

Comme vous pouvez le voir, si le nombre incorrect d'éléments se trouve dans le conteneur splatté, alors l'appel de fonction échouera, tout comme s'il y avait trop d'arguments donnés explicitement.

## Optional Arguments

Il est souvent possible de fournir des valeurs par défaut sensées pour les arguments de fonction. Cela peut éviter aux utilisateurs de devoir passer chaque argument à chaque appel. Par exemple, la fonction [`Date(y, [m, d])`](@ref) du module `Dates` construit un type `Date` pour une année donnée `y`, un mois `m` et un jour `d`. Cependant, les arguments `m` et `d` sont optionnels et leur valeur par défaut est `1`. Ce comportement peut être exprimé de manière concise comme :

```jldoctest date_default_args
julia> using Dates

julia> function date(y::Int64, m::Int64=1, d::Int64=1)
           err = Dates.validargs(Date, y, m, d)
           err === nothing || throw(err)
           return Date(Dates.UTD(Dates.totaldays(y, m, d)))
       end
date (generic function with 3 methods)
```

Observez que cette définition appelle une autre méthode de la fonction `Date` qui prend un argument de type `UTInstant{Day}`.

Avec cette définition, la fonction peut être appelée avec un, deux ou trois arguments, et `1` est automatiquement passé lorsque seulement un ou deux des arguments sont spécifiés :

```jldoctest date_default_args
julia> date(2000, 12, 12)
2000-12-12

julia> date(2000, 12)
2000-12-01

julia> date(2000)
2000-01-01
```

Les arguments optionnels sont en réalité une syntaxe pratique pour écrire plusieurs définitions de méthode avec un nombre différent d'arguments (voir [Note on Optional and keyword Arguments](@ref)). Cela peut être vérifié pour notre exemple de fonction `date` en appelant la fonction `methods` :

```julia-repl
julia> methods(date)
# 3 methods for generic function "date":
[1] date(y::Int64) in Main at REPL[1]:1
[2] date(y::Int64, m::Int64) in Main at REPL[1]:1
[3] date(y::Int64, m::Int64, d::Int64) in Main at REPL[1]:1
```

## Keyword Arguments

Certaines fonctions nécessitent un grand nombre d'arguments ou ont un grand nombre de comportements. Se souvenir de la façon d'appeler de telles fonctions peut être difficile. Les arguments nommés peuvent rendre ces interfaces complexes plus faciles à utiliser et à étendre en permettant d'identifier les arguments par leur nom plutôt que seulement par leur position.

Par exemple, considérons une fonction `plot` qui trace une ligne. Cette fonction peut avoir de nombreuses options pour contrôler le style de ligne, la largeur, la couleur, etc. Si elle accepte des arguments nommés, un appel possible pourrait ressembler à `plot(x, y, width=2)`, où nous avons choisi de spécifier uniquement la largeur de la ligne. Remarquez que cela sert deux objectifs. L'appel est plus facile à lire, car nous pouvons étiqueter un argument avec sa signification. Il devient également possible de passer n'importe quel sous-ensemble d'un grand nombre d'arguments, dans n'importe quel ordre.

Les fonctions avec des arguments de mot-clé sont définies en utilisant un point-virgule dans la signature :

```julia
function plot(x, y; style="solid", width=1, color="black")
    ###
end
```

Lorsque la fonction est appelée, le point-virgule est optionnel : on peut soit appeler `plot(x, y, width=2)`, soit `plot(x, y; width=2)`, mais le premier style est plus courant. Un point-virgule explicite est requis uniquement pour passer des varargs ou des mots-clés calculés comme décrit ci-dessous.

Les valeurs par défaut des arguments de mot-clé ne sont évaluées que lorsque cela est nécessaire (lorsqu'un argument de mot-clé correspondant n'est pas passé), et dans l'ordre de gauche à droite. Par conséquent, les expressions par défaut peuvent faire référence à des arguments de mot-clé précédents.

Les types d'arguments de mot-clé peuvent être rendus explicites comme suit :

```julia
function f(; x::Int=1)
    ###
end
```

Les arguments de mot-clé peuvent également être utilisés dans les fonctions varargs :

```julia
function plot(x...; style="solid")
    ###
end
```

Les arguments supplémentaires peuvent être collectés en utilisant `...`, comme dans les fonctions varargs :

```julia
function f(x; y=0, kwargs...)
    ###
end
```

À l'intérieur de `f`, `kwargs` sera un itérateur clé-valeur immuable sur un tuple nommé. Les tuples nommés (ainsi que les dictionnaires avec des clés de `Symbol`, et d'autres itérateurs produisant des collections à deux valeurs avec un symbole comme première valeur) peuvent être passés en tant qu'arguments de mot-clé en utilisant un point-virgule dans un appel, par exemple `f(x, z=1; kwargs...)`.

Si un argument clé n'est pas assigné à une valeur par défaut dans la définition de la méthode, alors il est *requis* : une exception [`UndefKeywordError`](@ref) sera levée si l'appelant ne lui assigne pas de valeur :

```julia
function f(x; y)
    ###
end
f(3, y=5) # ok, y is assigned
f(3)      # throws UndefKeywordError(:y)
```

On peut également passer des expressions `clé => valeur` après un point-virgule. Par exemple, `plot(x, y; :width => 2)` est équivalent à `plot(x, y, width=2)`. Cela est utile dans des situations où le nom du mot-clé est calculé à l'exécution.

Lorsqu'un identifiant nu ou une expression par points apparaît après un point-virgule, le nom de l'argument clé est implicite par l'identifiant ou le nom du champ. Par exemple, `plot(x, y; width)` est équivalent à `plot(x, y; width=width)` et `plot(x, y; options.width)` est équivalent à `plot(x, y; width=options.width)`.

La nature des arguments de mot-clé permet de spécifier le même argument plusieurs fois. Par exemple, dans l'appel `plot(x, y; options..., width=2)`, il est possible que la structure `options` contienne également une valeur pour `width`. Dans ce cas, l'occurrence la plus à droite a la priorité ; dans cet exemple, `width` est certain d'avoir la valeur `2`. Cependant, spécifier explicitement le même argument de mot-clé plusieurs fois, par exemple `plot(x, y, width=2, width=3)`, n'est pas autorisé et entraîne une erreur de syntaxe.

## Evaluation Scope of Default Values

Lorsque les expressions par défaut des arguments optionnels et des arguments de mot-clé sont évaluées, seuls les *arguments précédents* sont dans le champ d'application. Par exemple, étant donné cette définition :

```julia
function f(x, a=b, b=1)
    ###
end
```

le `b` dans `a=b` fait référence à un `b` dans une portée extérieure, et non à l'argument suivant `b`.

## Do-Block Syntax for Function Arguments

Passer des fonctions en tant qu'arguments à d'autres fonctions est une technique puissante, mais la syntaxe pour cela n'est pas toujours pratique. De tels appels sont particulièrement difficiles à écrire lorsque l'argument de la fonction nécessite plusieurs lignes. Par exemple, considérons l'appel de [`map`](@ref) sur une fonction avec plusieurs cas :

```julia
map(x->begin
           if x < 0 && iseven(x)
               return 0
           elseif x == 0
               return 1
           else
               return x
           end
       end,
    [A, B, C])
```

Julia fournit un mot réservé `do` pour réécrire ce code de manière plus claire :

```julia
map([A, B, C]) do x
    if x < 0 && iseven(x)
        return 0
    elseif x == 0
        return 1
    else
        return x
    end
end
```

La syntaxe `do x` crée une fonction anonyme avec l'argument `x` et passe la fonction anonyme comme premier argument à la fonction "extérieure" - [`map`](@ref) dans cet exemple. De même, `do a,b` créerait une fonction anonyme à deux arguments. Notez que `do (a,b)` créerait une fonction anonyme à un argument, dont l'argument est un tuple à décomposer. Un simple `do` déclarerait que ce qui suit est une fonction anonyme de la forme `() -> ...`.

Comment ces arguments sont initialisés dépend de la fonction "extérieure" ; ici, [`map`](@ref) va successivement définir `x` à `A`, `B`, `C`, en appelant la fonction anonyme à chaque fois, tout comme cela se produirait dans la syntaxe `map(func, [A, B, C])`.

Cette syntaxe facilite l'utilisation des fonctions pour étendre efficacement le langage, car les appels ressemblent à des blocs de code normaux. Il existe de nombreuses utilisations possibles très différentes de [`map`](@ref), comme la gestion de l'état du système. Par exemple, il existe une version de [`open`](@ref) qui exécute du code garantissant que le fichier ouvert est finalement fermé :

```julia
open("outfile", "w") do io
    write(io, data)
end
```

Ceci est accompli par la définition suivante :

```julia
function open(f::Function, args...)
    io = open(args...)
    try
        f(io)
    finally
        close(io)
    end
end
```

Ici, [`open`](@ref) ouvre d'abord le fichier pour écriture, puis passe le flux de sortie résultant à la fonction anonyme que vous avez définie dans le bloc `do ... end`. Après la sortie de votre fonction, `4d61726b646f776e2e436f64652822222c20226f70656e2229_40726566` s'assurera que le flux est correctement fermé, que votre fonction se soit terminée normalement ou ait levé une exception. (La construction `try/finally` sera décrite dans [Control Flow](@ref).)

Avec la syntaxe du bloc `do`, il est utile de consulter la documentation ou l'implémentation pour savoir comment les arguments de la fonction utilisateur sont initialisés.

Un bloc `do`, comme toute autre fonction interne, peut "capturer" des variables de son environnement. Par exemple, la variable `data` dans l'exemple ci-dessus de `open...do` est capturée de l'environnement extérieur. Les variables capturées peuvent créer des défis de performance comme discuté dans [performance tips](@ref man-performance-captured).

## Function composition and piping

Les fonctions en Julia peuvent être combinées en les composant ou en les enchaînant (piping).

La composition de fonctions est lorsque vous combinez des fonctions ensemble et appliquez la composition résultante à des arguments. Vous utilisez l'opérateur de composition de fonctions (`∘`) pour composer les fonctions, donc `(f ∘ g)(args...; kw...)` est équivalent à `f(g(args...; kw...))`.

Vous pouvez taper l'opérateur de composition dans le REPL et les éditeurs configurés de manière appropriée en utilisant `\circ<tab>`.

Par exemple, les fonctions `sqrt` et `+` peuvent être composées comme ceci :

```jldoctest
julia> (sqrt ∘ +)(3, 6)
3.0
```

Cela additionne d'abord les nombres, puis trouve la racine carrée du résultat.

L'exemple suivant compose trois fonctions et applique le résultat sur un tableau de chaînes :

```jldoctest
julia> map(first ∘ reverse ∘ uppercase, split("you can compose functions like this"))
6-element Vector{Char}:
 'U': ASCII/Unicode U+0055 (category Lu: Letter, uppercase)
 'N': ASCII/Unicode U+004E (category Lu: Letter, uppercase)
 'E': ASCII/Unicode U+0045 (category Lu: Letter, uppercase)
 'S': ASCII/Unicode U+0053 (category Lu: Letter, uppercase)
 'E': ASCII/Unicode U+0045 (category Lu: Letter, uppercase)
 'S': ASCII/Unicode U+0053 (category Lu: Letter, uppercase)
```

Le chaînage de fonctions (parfois appelé "piping" ou "utiliser un pipe" pour envoyer des données à une fonction suivante) est lorsque vous appliquez une fonction à la sortie de la fonction précédente :

```jldoctest
julia> 1:10 |> sum |> sqrt
7.416198487095663
```

Ici, le total produit par `sum` est passé à la fonction `sqrt`. La composition équivalente serait :

```jldoctest
julia> (sqrt ∘ sum)(1:10)
7.416198487095663
```

L'opérateur pipe peut également être utilisé avec le broadcasting, sous la forme `.|>`, pour fournir une combinaison utile de la syntaxe de chaînage/piping et de la vectorisation par point (décrite ci-dessous).

```jldoctest
julia> ["a", "list", "of", "strings"] .|> [uppercase, reverse, titlecase, length]
4-element Vector{Any}:
  "A"
  "tsil"
  "Of"
 7
```

Lorsque vous combinez des tuyaux avec des fonctions anonymes, des parenthèses doivent être utilisées si les tuyaux suivants ne doivent pas être analysés comme faisant partie du corps de la fonction anonyme. Comparez :

```jldoctest
julia> 1:3 .|> (x -> x^2) |> sum |> sqrt
3.7416573867739413

julia> 1:3 .|> x -> x^2 |> sum |> sqrt
3-element Vector{Float64}:
 1.0
 2.0
 3.0
```

## [Dot Syntax for Vectorizing Functions](@id man-vectorized)

Dans les langages de calcul technique, il est courant d'avoir des versions "vectorisées" de fonctions, qui appliquent simplement une fonction donnée `f(x)` à chaque élément d'un tableau `A` pour produire un nouveau tableau via `f(A)`. Ce type de syntaxe est pratique pour le traitement des données, mais dans d'autres langages, la vectorisation est également souvent nécessaire pour la performance : si les boucles sont lentes, la version "vectorisée" d'une fonction peut appeler un code de bibliothèque rapide écrit dans un langage de bas niveau. En Julia, les fonctions vectorisées ne sont *pas* nécessaires pour la performance, et en effet, il est souvent bénéfique d'écrire vos propres boucles (voir [Performance Tips](@ref man-performance-tips)), mais elles peuvent tout de même être pratiques. Par conséquent, *toute* fonction Julia `f` peut être appliquée élément par élément à n'importe quel tableau (ou autre collection) avec la syntaxe `f.(A)`. Par exemple, `sin` peut être appliqué à tous les éléments du vecteur `A` comme suit :

```jldoctest
julia> A = [1.0, 2.0, 3.0]
3-element Vector{Float64}:
 1.0
 2.0
 3.0

julia> sin.(A)
3-element Vector{Float64}:
 0.8414709848078965
 0.9092974268256817
 0.1411200080598672
```

Bien sûr, vous pouvez omettre le point si vous écrivez une méthode "vectorielle" spécialisée de `f`, par exemple via `f(A::AbstractArray) = map(f, A)`, et cela est tout aussi efficace que `f.(A)`. L'avantage de la syntaxe `f.(A)` est que les fonctions qui peuvent être vectorisées n'ont pas besoin d'être décidées à l'avance par l'auteur de la bibliothèque.

Plus généralement, `f.(args...)` est en réalité équivalent à `broadcast(f, args...)`, ce qui vous permet d'opérer sur plusieurs tableaux (même de formes différentes), ou un mélange de tableaux et de scalaires (voir [Broadcasting](@ref)). Par exemple, si vous avez `f(x, y) = 3x + 4y`, alors `f.(pi, A)` renverra un nouveau tableau consistant en `f(pi,a)` pour chaque `a` dans `A`, et `f.(vector1, vector2)` renverra un nouveau vecteur consistant en `f(vector1[i], vector2[i])` pour chaque index `i` (générant une exception si les vecteurs ont des longueurs différentes).

```jldoctest
julia> f(x, y) = 3x + 4y;

julia> A = [1.0, 2.0, 3.0];

julia> B = [4.0, 5.0, 6.0];

julia> f.(pi, A)
3-element Vector{Float64}:
 13.42477796076938
 17.42477796076938
 21.42477796076938

julia> f.(A, B)
3-element Vector{Float64}:
 19.0
 26.0
 33.0
```

Les arguments de mot-clé ne sont pas diffusés, mais sont simplement transmis à chaque appel de la fonction. Par exemple, `round.(x, digits=3)` est équivalent à `broadcast(x -> round(x, digits=3), x)`.

De plus, les appels `f.(args...)` *imbriqués* sont *fusionnés* en une seule boucle de `broadcast`. Par exemple, `sin.(cos.(X))` est équivalent à `broadcast(x -> sin(cos(x)), X)`, similaire à `[sin(cos(x)) for x in X]` : il n'y a qu'une seule boucle sur `X`, et un seul tableau est alloué pour le résultat. [En revanche, `sin(cos(X))` dans un langage "vectorisé" typique allouerait d'abord un tableau temporaire pour `tmp=cos(X)`, puis calculerait `sin(tmp)` dans une boucle séparée, allouant un second tableau.] Cette fusion de boucles n'est pas une optimisation du compilateur qui peut ou non se produire, c'est une *garantie syntaxique* chaque fois que des appels `f.(args...)` imbriqués sont rencontrés. Techniquement, la fusion s'arrête dès qu'un appel de fonction "non-dot" est rencontré ; par exemple, dans `sin.(sort(cos.(X)))`, les boucles `sin` et `cos` ne peuvent pas être fusionnées en raison de la fonction `sort` intervenante.

Enfin, l'efficacité maximale est généralement atteinte lorsque le tableau de sortie d'une opération vectorisée est *pré-alloué*, de sorte que les appels répétés n'allouent pas de nouveaux tableaux encore et encore pour les résultats (voir [Pre-allocating outputs](@ref)). Une syntaxe pratique pour cela est `X .= ...`, qui est équivalente à `broadcast!(identity, X, ...)` sauf que, comme ci-dessus, la boucle `broadcast!` est fusionnée avec tous les appels "point" imbriqués. Par exemple, `X .= sin.(Y)` est équivalent à `broadcast!(sin, X, Y)`, écrasant `X` avec `sin.(Y)` sur place. Si le côté gauche est une expression d'indexation de tableau, par exemple `X[begin+1:end] .= sin.(Y)`, alors cela se traduit par `broadcast!` sur une `view`, par exemple `broadcast!(sin, view(X, firstindex(X)+1:lastindex(X)), Y)`, de sorte que le côté gauche soit mis à jour sur place.

Puisque l'ajout de points à de nombreuses opérations et appels de fonction dans une expression peut être fastidieux et conduire à un code difficile à lire, la macro [`@.`](@ref @__dot__) est fournie pour convertir *chaque* appel de fonction, opération et affectation dans une expression en la version "pointée".

```jldoctest
julia> Y = [1.0, 2.0, 3.0, 4.0];

julia> X = similar(Y); # pre-allocate output array

julia> @. X = sin(cos(Y)) # equivalent to X .= sin.(cos.(Y))
4-element Vector{Float64}:
  0.5143952585235492
 -0.4042391538522658
 -0.8360218615377305
 -0.6080830096407656
```

Les opérateurs binaires (ou unaires) comme `.+` sont gérés avec le même mécanisme : ils sont équivalents à des appels de `broadcast` et sont fusionnés avec d'autres appels "dot" imbriqués. `X .+= Y` etc. est équivalent à `X .= X .+ Y` et résulte en une affectation en place fusionnée ; voir aussi [dot operators](@ref man-dot-operators).

Vous pouvez également combiner des opérations de point avec des chaînes de fonctions en utilisant [`|>`](@ref), comme dans cet exemple :

```jldoctest
julia> 1:5 .|> [x->x^2, inv, x->2*x, -, isodd]
5-element Vector{Real}:
    1
    0.5
    6
   -4
 true
```

Toutes les fonctions dans le broadcast fusionné sont toujours appelées pour chaque élément du résultat. Ainsi, `X .+ σ .* randn.()` ajoutera un masque de valeurs aléatoires indépendantes et identiquement échantillonnées à chaque élément du tableau `X`, mais `X .+ σ .* randn()` ajoutera le *même* échantillon aléatoire à chaque élément. Dans les cas où le calcul fusionné est constant le long d'un ou plusieurs axes de l'itération de broadcast, il peut être possible de tirer parti d'un compromis espace-temps et d'allouer des valeurs intermédiaires pour réduire le nombre de calculs. Voir plus à [performance tips](@ref man-performance-unfuse).

## Further Reading

Nous devrions mentionner ici que cela est loin de donner une image complète de la définition des fonctions. Julia a un système de types sophistiqué et permet le dispatch multiple sur les types d'arguments. Aucun des exemples donnés ici ne fournit d'annotations de type sur leurs arguments, ce qui signifie qu'ils sont applicables à tous les types d'arguments. Le système de types est décrit dans [Types](@ref man-types) et la définition d'une fonction en termes de méthodes choisies par dispatch multiple sur les types d'arguments à l'exécution est décrite dans [Methods](@ref).
