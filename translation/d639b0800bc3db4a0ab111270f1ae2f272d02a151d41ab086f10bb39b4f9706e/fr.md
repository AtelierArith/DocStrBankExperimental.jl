# Control Flow

Julia fournit une variété de constructions de contrôle de flux :

  * [Compound Expressions](@ref man-compound-expressions): `début` et `;`.
  * [Conditional Evaluation](@ref man-conditional-evaluation): `si`-`sinon si`-`sinon` et `?:` (opérateur ternaire).
  * [Short-Circuit Evaluation](@ref): opérateurs logiques `&&` (“et”) et `||` (“ou”), ainsi que des comparaisons en chaîne.
  * [Repeated Evaluation: Loops](@ref man-loops): `tant que` et `pour`.
  * [Exception Handling](@ref): `essayer`-`attraper`, [`error`](@ref) et [`throw`](@ref).
  * [Tasks (aka Coroutines)](@ref man-tasks): [`yieldto`](@ref).

Les cinq premiers mécanismes de contrôle de flux sont standards dans les langages de programmation de haut niveau. [`Task`](@ref) ne sont pas si standards : ils fournissent un contrôle de flux non local, rendant possible le passage entre des calculs temporairement suspendus. C'est une construction puissante : à la fois la gestion des exceptions et le multitâche coopératif sont implémentés en Julia en utilisant des tâches. La programmation quotidienne ne nécessite pas d'utilisation directe des tâches, mais certains problèmes peuvent être résolus beaucoup plus facilement en utilisant des tâches.

## [Compound Expressions](@id man-compound-expressions)

Parfois, il est pratique d'avoir une seule expression qui évalue plusieurs sous-expressions dans l'ordre, renvoyant la valeur de la dernière sous-expression comme sa valeur. Il existe deux constructions Julia qui accomplissent cela : les blocs `begin` et les chaînes `;`. La valeur des deux constructions d'expressions composées est celle de la dernière sous-expression. Voici un exemple d'un bloc `begin` :

```jldoctest
julia> z = begin
           x = 1
           y = 2
           x + y
       end
3
```

Puisque ce sont des expressions assez petites et simples, elles pourraient facilement être placées sur une seule ligne, c'est là que la syntaxe de chaîne `;` est utile :

```jldoctest
julia> z = (x = 1; y = 2; x + y)
3
```

Cette syntaxe est particulièrement utile avec la forme de définition de fonction sur une seule ligne introduite dans [Functions](@ref man-functions). Bien que cela soit typique, il n'y a aucune exigence pour que les blocs `begin` soient multilignes ou que les chaînes `;` soient sur une seule ligne :

```jldoctest
julia> begin x = 1; y = 2; x + y end
3

julia> (x = 1;
        y = 2;
        x + y)
3
```

## [Conditional Evaluation](@id man-conditional-evaluation)

L'évaluation conditionnelle permet à des portions de code d'être évaluées ou non en fonction de la valeur d'une expression booléenne. Voici l'anatomie de la syntaxe conditionnelle `if`-`elseif`-`else` :

```julia
if x < y
    println("x is less than y")
elseif x > y
    println("x is greater than y")
else
    println("x is equal to y")
end
```

Si l'expression de condition `x < y` est `true`, alors le bloc correspondant est évalué ; sinon, l'expression de condition `x > y` est évaluée, et si elle est `true`, le bloc correspondant est évalué ; si aucune des expressions n'est vraie, le bloc `else` est évalué. Voici comment cela fonctionne :

```jldoctest
julia> function test(x, y)
           if x < y
               println("x is less than y")
           elseif x > y
               println("x is greater than y")
           else
               println("x is equal to y")
           end
       end
test (generic function with 1 method)

julia> test(1, 2)
x is less than y

julia> test(2, 1)
x is greater than y

julia> test(1, 1)
x is equal to y
```

Les blocs `elseif` et `else` sont optionnels, et autant de blocs `elseif` que souhaité peuvent être utilisés. Les expressions de condition dans la construction `if`-`elseif`-`else` sont évaluées jusqu'à ce que la première évalue à `true`, après quoi le bloc associé est évalué, et aucune autre expression de condition ou bloc n'est évalué.

Les blocs `if` sont "fuyants", c'est-à-dire qu'ils n'introduisent pas de portée locale. Cela signifie que les nouvelles variables définies à l'intérieur des clauses `if` peuvent être utilisées après le bloc `if`, même si elles n'étaient pas définies auparavant. Ainsi, nous aurions pu définir la fonction `test` ci-dessus comme

```jldoctest
julia> function test(x,y)
           if x < y
               relation = "less than"
           elseif x == y
               relation = "equal to"
           else
               relation = "greater than"
           end
           println("x is ", relation, " y.")
       end
test (generic function with 1 method)

julia> test(2, 1)
x is greater than y.
```

La variable `relation` est déclarée à l'intérieur du bloc `if`, mais utilisée à l'extérieur. Cependant, lorsque vous dépendez de ce comportement, assurez-vous que tous les chemins de code possibles définissent une valeur pour la variable. Le changement suivant à la fonction ci-dessus entraîne une erreur d'exécution.

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> function test(x,y)
           if x < y
               relation = "less than"
           elseif x == y
               relation = "equal to"
           end
           println("x is ", relation, " y.")
       end
test (generic function with 1 method)

julia> test(1,2)
x is less than y.

julia> test(2,1)
ERROR: UndefVarError: `relation` not defined in local scope
Stacktrace:
 [1] test(::Int64, ::Int64) at ./none:7
```

Les blocs `if` retournent également une valeur, ce qui peut sembler contre-intuitif pour les utilisateurs venant de nombreux autres langages. Cette valeur est simplement la valeur de retour de la dernière instruction exécutée dans la branche qui a été choisie, donc

```jldoctest
julia> x = 3
3

julia> if x > 0
           "positive!"
       else
           "negative..."
       end
"positive!"
```

Notez que les très courtes instructions conditionnelles (en une ligne) sont souvent exprimées en utilisant l'évaluation à court-circuit en Julia, comme décrit dans la section suivante.

Contrairement à C, MATLAB, Perl, Python et Ruby – mais comme Java et quelques autres langages plus stricts et typés – il est considéré comme une erreur si la valeur d'une expression conditionnelle n'est pas `true` ou `false` :

```jldoctest
julia> if 1
           println("true")
       end
ERROR: TypeError: non-boolean (Int64) used in boolean context
```

Cette erreur indique que la condition était du mauvais type : [`Int64`](@ref) plutôt que le requis [`Bool`](@ref).

L'opérateur "ternaire" appelé `?:` est étroitement lié à la syntaxe `if`-`elseif`-`else`, mais est utilisé là où un choix conditionnel entre des valeurs d'expression uniques est requis, contrairement à l'exécution conditionnelle de blocs de code plus longs. Il tire son nom du fait qu'il est le seul opérateur dans la plupart des langages à prendre trois opérandes :

```julia
a ? b : c
```

L'expression `a`, avant le `?`, est une expression conditionnelle, et l'opération ternaire évalue l'expression `b`, avant le `:`, si la condition `a` est `true` ou l'expression `c`, après le `:`, si elle est `false`. Notez que les espaces autour de `?` et `:` sont obligatoires : une expression comme `a?b:c` n'est pas une expression ternaire valide (mais un saut de ligne est acceptable après le `?` et le `:`).

La façon la plus simple de comprendre ce comportement est de voir un exemple. Dans l'exemple précédent, l'appel `println` est partagé par les trois branches : le seul véritable choix est quelle chaîne littérale imprimer. Cela pourrait être écrit de manière plus concise en utilisant l'opérateur ternaire. Pour des raisons de clarté, essayons d'abord une version à deux voies :

```jldoctest
julia> x = 1; y = 2;

julia> println(x < y ? "less than" : "not less than")
less than

julia> x = 1; y = 0;

julia> println(x < y ? "less than" : "not less than")
not less than
```

Si l'expression `x < y` est vraie, l'ensemble de l'expression de l'opérateur ternaire évalue à la chaîne `"moins que"` et sinon elle évalue à la chaîne `"pas moins que"`. L'exemple original à trois voies nécessite de chaîner plusieurs utilisations de l'opérateur ternaire ensemble :

```jldoctest
julia> test(x, y) = println(x < y ? "x is less than y"    :
                            x > y ? "x is greater than y" : "x is equal to y")
test (generic function with 1 method)

julia> test(1, 2)
x is less than y

julia> test(2, 1)
x is greater than y

julia> test(1, 1)
x is equal to y
```

Pour faciliter l'enchaînement, l'opérateur s'associe de droite à gauche.

Il est significatif que, comme pour `if`-`elseif`-`else`, les expressions avant et après le `:` ne sont évaluées que si l'expression conditionnelle évalue à `true` ou `false`, respectivement :

```jldoctest
julia> v(x) = (println(x); x)
v (generic function with 1 method)

julia> 1 < 2 ? v("yes") : v("no")
yes
"yes"

julia> 1 > 2 ? v("yes") : v("no")
no
"no"
```

## Short-Circuit Evaluation

Les opérateurs `&&` et `||` en Julia correspondent respectivement aux opérations logiques "et" et "ou", et sont généralement utilisés à cette fin. Cependant, ils ont une propriété supplémentaire d'évaluation *à court-circuit* : ils n'évaluent pas nécessairement leur deuxième argument, comme expliqué ci-dessous. (Il existe également des opérateurs bit à bit `&` et `|` qui peuvent être utilisés comme "et" et "ou" logiques *sans* comportement de court-circuit, mais attention, `&` et `|` ont une priorité plus élevée que `&&` et `||` pour l'ordre d'évaluation.)

L'évaluation par court-circuit est assez similaire à l'évaluation conditionnelle. Ce comportement se retrouve dans la plupart des langages de programmation impératifs ayant les opérateurs booléens `&&` et `||` : dans une série d'expressions booléennes reliées par ces opérateurs, seul le nombre minimum d'expressions est évalué pour déterminer la valeur booléenne finale de l'ensemble de la chaîne. Certains langages (comme Python) les appellent `and` (`&&`) et `or` (`||`). Explicitement, cela signifie que :

  * Dans l'expression `a && b`, la sous-expression `b` n'est évaluée que si `a` évalue à `true`.
  * Dans l'expression `a || b`, la sous-expression `b` n'est évaluée que si `a` évalue à `false`.

Le raisonnement est que `a && b` doit être `false` si `a` est `false`, peu importe la valeur de `b`, et de même, la valeur de `a || b` doit être `true` si `a` est `true`, peu importe la valeur de `b`. Les deux `&&` et `||` s'associent à droite, mais `&&` a une priorité plus élevée que `||`. Il est facile d'expérimenter ce comportement :

```jldoctest tandf
julia> t(x) = (println(x); true)
t (generic function with 1 method)

julia> f(x) = (println(x); false)
f (generic function with 1 method)

julia> t(1) && t(2)
1
2
true

julia> t(1) && f(2)
1
2
false

julia> f(1) && t(2)
1
false

julia> f(1) && f(2)
1
false

julia> t(1) || t(2)
1
true

julia> t(1) || f(2)
1
true

julia> f(1) || t(2)
1
2
true

julia> f(1) || f(2)
1
2
false
```

Vous pouvez facilement expérimenter de la même manière avec l'associativité et la priorité de diverses combinaisons des opérateurs `&&` et `||`.

Ce comportement est fréquemment utilisé en Julia pour former une alternative aux très courtes instructions `if`. Au lieu de `if <cond> <statement> end`, on peut écrire `<cond> && <statement>` (qui pourrait être lu comme : <cond> *et ensuite* <statement>). De même, au lieu de `if ! <cond> <statement> end`, on peut écrire `<cond> || <statement>` (qui pourrait être lu comme : <cond> *ou sinon* <statement>).

Par exemple, une routine de factorielle récursive pourrait être définie comme ceci :

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> function fact(n::Int)
           n >= 0 || error("n must be non-negative")
           n == 0 && return 1
           n * fact(n-1)
       end
fact (generic function with 1 method)

julia> fact(5)
120

julia> fact(0)
1

julia> fact(-1)
ERROR: n must be non-negative
Stacktrace:
 [1] error at ./error.jl:33 [inlined]
 [2] fact(::Int64) at ./none:2
 [3] top-level scope
```

Les opérations booléennes *sans* évaluation par court-circuit peuvent être effectuées avec les opérateurs booléens bit à bit introduits dans [Mathematical Operations and Elementary Functions](@ref) : `&` et `|`. Ce sont des fonctions normales, qui prennent en charge la syntaxe d'opérateur infixe, mais évaluent toujours leurs arguments :

```jldoctest tandf
julia> f(1) & t(2)
1
2
false

julia> t(1) | t(2)
1
2
true
```

Tout comme les expressions conditionnelles utilisées dans `if`, `elseif` ou l'opérateur ternaire, les opérandes de `&&` ou `||` doivent être des valeurs booléennes (`true` ou `false`). Utiliser une valeur non booléenne n'importe où sauf pour la dernière entrée dans une chaîne conditionnelle est une erreur :

```jldoctest
julia> 1 && true
ERROR: TypeError: non-boolean (Int64) used in boolean context
```

D'autre part, tout type d'expression peut être utilisé à la fin d'une chaîne conditionnelle. Elle sera évaluée et renvoyée en fonction des conditions précédentes :

```jldoctest
julia> true && (x = (1, 2, 3))
(1, 2, 3)

julia> false && (x = (1, 2, 3))
false
```

## [Repeated Evaluation: Loops](@id man-loops)

Il existe deux constructions pour l'évaluation répétée d'expressions : la boucle `while` et la boucle `for`. Voici un exemple d'une boucle `while` :

```jldoctest
julia> i = 1;

julia> while i <= 3
           println(i)
           global i += 1
       end
1
2
3
```

La boucle `while` évalue l'expression de condition (`i <= 3` dans ce cas), et tant qu'elle reste `true`, elle continue également à évaluer le corps de la boucle `while`. Si l'expression de condition est `false` lorsque la boucle `while` est atteinte pour la première fois, le corps n'est jamais évalué.

La boucle `for` rend plus facile l'écriture d'idiomes d'évaluation répétés courants. Comme le comptage vers le haut et vers le bas, comme dans la boucle `while` ci-dessus, est si courant, il peut être exprimé de manière plus concise avec une boucle `for` :

```jldoctest
julia> for i = 1:3
           println(i)
       end
1
2
3
```

Ici, le `1:3` est un objet [`range`](@ref), représentant la séquence de nombres 1, 2, 3. La boucle `for` itère à travers ces valeurs, assignant chacune d'elles à la variable `i`. En général, la construction `for` peut boucler sur tout objet "itérable" (ou "conteneur"), d'une plage comme `1:3` ou `1:3:13` (un [`StepRange`](@ref) indiquant chaque 3ème entier 1, 4, 7, …, 13) à des conteneurs plus génériques comme des tableaux, y compris [iterators defined by user code](@ref man-interface-iteration) ou des packages externes. Pour les conteneurs autres que les plages, le mot-clé alternatif (mais entièrement équivalent) `in` ou `∈` est généralement utilisé à la place de `=`, car cela rend le code plus clair :

```jldoctest
julia> for i in [1,4,0]
           println(i)
       end
1
4
0

julia> for s ∈ ["foo","bar","baz"]
           println(s)
       end
foo
bar
baz
```

Différents types de conteneurs itérables seront introduits et discutés dans les sections suivantes du manuel (voir, par exemple, [Multi-dimensional Arrays](@ref man-multi-dim-arrays)).

Une distinction plutôt importante entre la forme de boucle `while` précédente et la forme de boucle `for` est la portée pendant laquelle la variable est visible. Une boucle `for` introduit toujours une nouvelle variable d'itération dans son corps, peu importe si une variable du même nom existe dans la portée englobante. Cela implique que, d'une part, `i` n'a pas besoin d'être déclarée avant la boucle. D'autre part, elle ne sera pas visible en dehors de la boucle, ni une variable extérieure du même nom ne sera affectée. Vous aurez besoin soit d'une nouvelle instance de session interactive, soit d'un nom de variable différent pour tester cela :

```jldoctest
julia> for j = 1:3
           println(j)
       end
1
2
3

julia> j
ERROR: UndefVarError: `j` not defined in `Main`
```

```jldoctest
julia> j = 0;

julia> for j = 1:3
           println(j)
       end
1
2
3

julia> j
0
```

Utilisez `for outer` pour modifier le comportement ultérieur et réutiliser une variable locale existante.

Voir [Scope of Variables](@ref scope-of-variables) pour une explication détaillée de la portée des variables, [`outer`](@ref), et comment cela fonctionne en Julia.

Il est parfois pratique de terminer la répétition d'un `while` avant que la condition de test ne soit falsifiée ou d'arrêter l'itération dans une boucle `for` avant que la fin de l'objet itérable ne soit atteinte. Cela peut être accompli avec le mot-clé `break` :

```jldoctest
julia> i = 1;

julia> while true
           println(i)
           if i >= 3
               break
           end
           global i += 1
       end
1
2
3

julia> for j = 1:1000
           println(j)
           if j >= 3
               break
           end
       end
1
2
3
```

Sans le mot-clé `break`, la boucle `while` ci-dessus ne se terminerait jamais d'elle-même, et la boucle `for` itérerait jusqu'à 1000. Ces boucles sont toutes deux quittées prématurément en utilisant `break`.

Dans d'autres circonstances, il est pratique de pouvoir arrêter une itération et passer immédiatement à la suivante. Le mot-clé `continue` accomplit cela :

```jldoctest
julia> for i = 1:10
           if i % 3 != 0
               continue
           end
           println(i)
       end
3
6
9
```

Ceci est un exemple quelque peu artificiel puisque nous pourrions produire le même comportement plus clairement en niant la condition et en plaçant l'appel `println` à l'intérieur du bloc `if`. Dans une utilisation réaliste, il y a plus de code à évaluer après le `continue`, et il y a souvent plusieurs points à partir desquels on appelle `continue`.

Plusieurs boucles `for` imbriquées peuvent être combinées en une seule boucle externe, formant le produit cartésien de ses itérables :

```jldoctest
julia> for i = 1:2, j = 3:4
           println((i, j))
       end
(1, 3)
(1, 4)
(2, 3)
(2, 4)
```

Avec cette syntaxe, les itérables peuvent toujours faire référence aux variables de la boucle externe ; par exemple, `for i = 1:n, j = 1:i` est valide. Cependant, une instruction `break` à l'intérieur de cette boucle sort de l'ensemble de la nest de boucles, et pas seulement de la boucle intérieure. Les deux variables (`i` et `j`) sont définies avec leurs valeurs d'itération actuelles chaque fois que la boucle intérieure s'exécute. Par conséquent, les affectations à `i` ne seront pas visibles pour les itérations suivantes :

```jldoctest
julia> for i = 1:2, j = 3:4
           println((i, j))
           i = 0
       end
(1, 3)
(1, 4)
(2, 3)
(2, 4)
```

Si cet exemple était réécrit pour utiliser un mot-clé `for` pour chaque variable, alors la sortie serait différente : les deuxième et quatrième valeurs contiendraient `0`.

Plusieurs conteneurs peuvent être itérés en même temps dans une seule boucle `for` en utilisant [`zip`](@ref) :

```jldoctest
julia> for (j, k) in zip([1 2 3], [4 5 6 7])
           println((j,k))
       end
(1, 4)
(2, 5)
(3, 6)
```

En utilisant [`zip`](@ref), vous créerez un itérateur qui est un tuple contenant les sous-itérateurs pour les conteneurs qui lui sont passés. L'itérateur `zip` itérera sur tous les sous-itérateurs dans l'ordre, choisissant le $i$ème élément de chaque sous-itérateur lors de la $i$ème itération de la boucle `for`. Une fois que l'un des sous-itérateurs est épuisé, la boucle `for` s'arrêtera.

## Exception Handling

Lorsque qu'une condition inattendue se produit, une fonction peut être incapable de renvoyer une valeur raisonnable à son appelant. Dans de tels cas, il peut être préférable que la condition exceptionnelle termine le programme tout en imprimant un message d'erreur de diagnostic, ou si le programmeur a fourni du code pour gérer de telles circonstances exceptionnelles, alors permettre à ce code de prendre les mesures appropriées.

### Built-in `Exception`s

Les `Exception`s sont lancées lorsqu'une condition inattendue s'est produite. Les `Exception`s intégrées énumérées ci-dessous interrompent toutes le flux normal de contrôle.

| `Exception`                   |
|:----------------------------- |
| [`ArgumentError`](@ref)       |
| [`BoundsError`](@ref)         |
| [`CompositeException`](@ref)  |
| [`DimensionMismatch`](@ref)   |
| [`DivideError`](@ref)         |
| [`DomainError`](@ref)         |
| [`EOFError`](@ref)            |
| [`ErrorException`](@ref)      |
| [`InexactError`](@ref)        |
| [`InitError`](@ref)           |
| [`InterruptException`](@ref)  |
| `InvalidStateException`       |
| [`KeyError`](@ref)            |
| [`LoadError`](@ref)           |
| [`OutOfMemoryError`](@ref)    |
| [`ReadOnlyMemoryError`](@ref) |
| [`RemoteException`](@ref)     |
| [`MethodError`](@ref)         |
| [`OverflowError`](@ref)       |
| [`Meta.ParseError`](@ref)     |
| [`SystemError`](@ref)         |
| [`TypeError`](@ref)           |
| [`UndefRefError`](@ref)       |
| [`UndefVarError`](@ref)       |
| [`StringIndexError`](@ref)    |

Par exemple, la fonction [`sqrt`](@ref) génère une [`DomainError`](@ref) si elle est appliquée à une valeur réelle négative :

```jldoctest
julia> sqrt(-1)
ERROR: DomainError with -1.0:
sqrt was called with a negative real argument but will only return a complex result if called with a complex argument. Try sqrt(Complex(x)).
Stacktrace:
[...]
```

Vous pouvez définir vos propres exceptions de la manière suivante :

```jldoctest
julia> struct MyCustomException <: Exception end
```

### The [`throw`](@ref) function

Les exceptions peuvent être créées explicitement avec [`throw`](@ref). Par exemple, une fonction définie uniquement pour les nombres non négatifs pourrait être écrite pour `4d61726b646f776e2e436f64652822222c20227468726f772229_40726566` un [`DomainError`](@ref) si l'argument est négatif :

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> f(x) = x>=0 ? exp(-x) : throw(DomainError(x, "argument must be non-negative"))
f (generic function with 1 method)

julia> f(1)
0.36787944117144233

julia> f(-1)
ERROR: DomainError with -1:
argument must be non-negative
Stacktrace:
 [1] f(::Int64) at ./none:1
```

Notez que [`DomainError`](@ref) sans parenthèses n'est pas une exception, mais un type d'exception. Il doit être appelé pour obtenir un objet `Exception` :

```jldoctest
julia> typeof(DomainError(nothing)) <: Exception
true

julia> typeof(DomainError) <: Exception
false
```

De plus, certains types d'exception prennent un ou plusieurs arguments qui sont utilisés pour le rapport d'erreurs :

```jldoctest
julia> throw(UndefVarError(:x))
ERROR: UndefVarError: `x` not defined
```

Ce mécanisme peut être facilement mis en œuvre par des types d'exception personnalisés suivant la manière dont [`UndefVarError`](@ref) est écrit :

```jldoctest
julia> struct MyUndefVarError <: Exception
           var::Symbol
       end

julia> Base.showerror(io::IO, e::MyUndefVarError) = print(io, e.var, " not defined")
```

!!! note
    Lors de la rédaction d'un message d'erreur, il est préférable de commencer le premier mot par une minuscule. Par exemple,

    `size(A) == size(B) || throw(DimensionMismatch("la taille de A n'est pas égale à la taille de B"))`

    est préféré par rapport à

    `size(A) == size(B) || throw(DimensionMismatch("La taille de A n'est pas égale à la taille de B"))`.

    Cependant, il est parfois logique de conserver la première lettre en majuscule, par exemple si un argument d'une fonction est une lettre majuscule :

    `size(A,1) == size(B,2) || throw(DimensionMismatch("A a une première dimension..."))`.


### Errors

La fonction [`error`](@ref) est utilisée pour produire un [`ErrorException`](@ref) qui interrompt le flux normal de contrôle.

Supposons que nous souhaitions arrêter l'exécution immédiatement si la racine carrée d'un nombre négatif est prise. Pour ce faire, nous pouvons définir une version floue de la fonction [`sqrt`](@ref) qui lève une erreur si son argument est négatif :

```jldoctest fussy_sqrt; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> fussy_sqrt(x) = x >= 0 ? sqrt(x) : error("negative x not allowed")
fussy_sqrt (generic function with 1 method)

julia> fussy_sqrt(2)
1.4142135623730951

julia> fussy_sqrt(-1)
ERROR: negative x not allowed
Stacktrace:
 [1] error at ./error.jl:33 [inlined]
 [2] fussy_sqrt(::Int64) at ./none:1
 [3] top-level scope
```

Si `fussy_sqrt` est appelé avec une valeur négative depuis une autre fonction, au lieu d'essayer de continuer l'exécution de la fonction appelante, il retourne immédiatement, affichant le message d'erreur dans la session interactive :

```jldoctest fussy_sqrt; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> function verbose_fussy_sqrt(x)
           println("before fussy_sqrt")
           r = fussy_sqrt(x)
           println("after fussy_sqrt")
           return r
       end
verbose_fussy_sqrt (generic function with 1 method)

julia> verbose_fussy_sqrt(2)
before fussy_sqrt
after fussy_sqrt
1.4142135623730951

julia> verbose_fussy_sqrt(-1)
before fussy_sqrt
ERROR: negative x not allowed
Stacktrace:
 [1] error at ./error.jl:33 [inlined]
 [2] fussy_sqrt at ./none:1 [inlined]
 [3] verbose_fussy_sqrt(::Int64) at ./none:3
 [4] top-level scope
```

### The `try/catch` statement

L'instruction `try/catch` permet de tester les `Exception`s et de gérer gracieusement les choses qui pourraient normalement faire planter votre application. Par exemple, dans le code ci-dessous, la fonction pour la racine carrée lancerait normalement une exception. En plaçant un bloc `try/catch` autour, nous pouvons atténuer cela ici. Vous pouvez choisir comment vous souhaitez gérer cette exception, que ce soit en la journalisant, en retournant une valeur de remplacement ou, comme dans le cas ci-dessous, où nous avons simplement imprimé une déclaration. Une chose à considérer lors de la décision sur la manière de gérer des situations inattendues est que l'utilisation d'un bloc `try/catch` est beaucoup plus lente que l'utilisation de la branche conditionnelle pour gérer ces situations. Ci-dessous, il y a plus d'exemples de gestion des exceptions avec un bloc `try/catch` :

```jldoctest
julia> try
           sqrt("ten")
       catch e
           println("You should have entered a numeric value")
       end
You should have entered a numeric value
```

Les instructions `try/catch` permettent également de sauvegarder l'`Exception` dans une variable. L'exemple artificiel suivant calcule la racine carrée du deuxième élément de `x` si `x` est indexable, sinon il suppose que `x` est un nombre réel et retourne sa racine carrée :

```jldoctest
julia> sqrt_second(x) = try
           sqrt(x[2])
       catch y
           if isa(y, DomainError)
               sqrt(complex(x[2], 0))
           elseif isa(y, BoundsError)
               sqrt(x)
           end
       end
sqrt_second (generic function with 1 method)

julia> sqrt_second([1 4])
2.0

julia> sqrt_second([1 -4])
0.0 + 2.0im

julia> sqrt_second(9)
3.0

julia> sqrt_second(-9)
ERROR: DomainError with -9.0:
sqrt was called with a negative real argument but will only return a complex result if called with a complex argument. Try sqrt(Complex(x)).
Stacktrace:
[...]
```

Notez que le symbole suivant `catch` sera toujours interprété comme un nom pour l'exception, donc il faut faire attention lors de l'écriture d'expressions `try/catch` sur une seule ligne. Le code suivant *ne* fonctionnera *pas* pour retourner la valeur de `x` en cas d'erreur :

```julia
try bad() catch x end
```

Au lieu de cela, utilisez un point-virgule ou insérez un saut de ligne après `catch` :

```julia
try bad() catch; x end

try bad()
catch
    x
end
```

Le pouvoir de la construction `try/catch` réside dans la capacité à dérouler immédiatement un calcul profondément imbriqué à un niveau beaucoup plus élevé dans la pile des fonctions appelantes. Il existe des situations où aucune erreur ne s'est produite, mais la capacité à dérouler la pile et à passer une valeur à un niveau supérieur est souhaitable. Julia fournit les fonctions [`rethrow`](@ref), [`backtrace`](@ref), [`catch_backtrace`](@ref) et [`current_exceptions`](@ref) pour une gestion des erreurs plus avancée.

### `else` Clauses

!!! compat "Julia 1.8"
    Cette fonctionnalité nécessite au moins Julia 1.8.


Dans certains cas, on peut non seulement vouloir gérer correctement le cas d'erreur, mais aussi vouloir exécuter du code uniquement si le bloc `try` réussit. Pour cela, une clause `else` peut être spécifiée après le bloc `catch`, qui est exécutée chaque fois qu'aucune erreur n'a été lancée précédemment. L'avantage par rapport à l'inclusion de ce code dans le bloc `try` est que d'autres erreurs ne sont pas silencieusement capturées par la clause `catch`.

```julia
local x
try
    x = read("file", String)
catch
    # handle read errors
else
    # do something with x
end
```

!!! note
    Les clauses `try`, `catch`, `else` et `finally` introduisent chacune leurs propres blocs de portée, donc si une variable est définie uniquement dans le bloc `try`, elle ne peut pas être accessible par la clause `else` ou `finally` :

    ```jldoctest
    julia> try
               foo = 1
           catch
           else
               foo
           end
    ERROR: UndefVarError: `foo` not defined in `Main`
    Suggestion: check for spelling errors or missing imports.
    ```

    Utilisez [`local` keyword](@ref local-scope) en dehors du bloc `try` pour rendre la variable accessible de n'importe où dans la portée extérieure.


### `finally` Clauses

Dans le code qui effectue des changements d'état ou utilise des ressources comme des fichiers, il y a généralement un travail de nettoyage (comme la fermeture de fichiers) qui doit être effectué lorsque le code est terminé. Les exceptions compliquent potentiellement cette tâche, car elles peuvent amener un bloc de code à sortir avant d'atteindre sa fin normale. Le mot-clé `finally` fournit un moyen d'exécuter un certain code lorsque un bloc de code donné se termine, peu importe comment il se termine.

Par exemple, voici comment nous pouvons garantir qu'un fichier ouvert est fermé :

```julia
f = open("file")
try
    # operate on file f
finally
    close(f)
end
```

Lorsque le contrôle quitte le bloc `try` (par exemple en raison d'un `return`, ou simplement en se terminant normalement), `close(f)` sera exécuté. Si le bloc `try` sort en raison d'une exception, l'exception continuera à se propager. Un bloc `catch` peut également être combiné avec `try` et `finally`. Dans ce cas, le bloc `finally` s'exécutera après que `catch` ait géré l'erreur.

## [Tasks (aka Coroutines)](@id man-tasks)

Les tâches sont une fonctionnalité de contrôle de flux qui permet de suspendre et de reprendre des calculs de manière flexible. Nous les mentionnons ici uniquement pour des raisons de complétude ; pour une discussion complète, voir [Asynchronous Programming](@ref man-asynchronous).
