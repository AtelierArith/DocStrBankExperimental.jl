# Metaprogramming

L'héritage le plus fort de Lisp dans le langage Julia est son support de la métaprogrammation. Comme Lisp, Julia représente son propre code sous forme de structure de données du langage lui-même. Puisque le code est représenté par des objets qui peuvent être créés et manipulés depuis l'intérieur du langage, il est possible pour un programme de transformer et de générer son propre code. Cela permet une génération de code sophistiquée sans étapes de construction supplémentaires, et permet également de véritables macros de style Lisp opérant au niveau de [abstract syntax trees](https://en.wikipedia.org/wiki/Abstract_syntax_tree). En revanche, les systèmes de "macro" de préprocesseur, comme ceux de C et C++, effectuent une manipulation et une substitution textuelles avant que toute analyse ou interprétation réelle n'ait lieu. Parce que tous les types de données et le code dans Julia sont représentés par des structures de données Julia, des capacités puissantes [reflection](https://en.wikipedia.org/wiki/Reflection_%28computer_programming%29) sont disponibles pour explorer les internes d'un programme et ses types tout comme n'importe quelle autre donnée.

!!! warning
    La métaprogrammation est un outil puissant, mais elle introduit une complexité qui peut rendre le code plus difficile à comprendre. Par exemple, il peut être étonnamment difficile d'obtenir les règles de portée correctes. La métaprogrammation ne devrait généralement être utilisée que lorsque d'autres approches telles que [higher order functions](@ref man-anonymous-functions) et [closures](https://en.wikipedia.org/wiki/Closure_(computer_programming)) ne peuvent pas être appliquées.

    `eval` et la définition de nouvelles macros devraient généralement être utilisés en dernier recours. Il est presque jamais une bonne idée d'utiliser `Meta.parse` ou de convertir une chaîne de caractères arbitraire en code Julia. Pour manipuler le code Julia, utilisez directement la structure de données `Expr` pour éviter la complexité de la façon dont la syntaxe Julia est analysée.

    Les meilleures utilisations de la métaprogrammation mettent souvent en œuvre la plupart de leur fonctionnalité dans des fonctions d'assistance à l'exécution, s'efforçant de minimiser la quantité de code qu'elles génèrent.


## Program representation

Chaque programme Julia commence sa vie en tant que chaîne :

```jldoctest prog
julia> prog = "1 + 1"
"1 + 1"
```

**Que se passe-t-il ensuite ?**

La prochaine étape consiste à [parse](https://en.wikipedia.org/wiki/Parsing#Computer_languages) chaque chaîne en un objet appelé une expression, représenté par le type Julia [`Expr`](@ref) :

```jldoctest prog
julia> ex1 = Meta.parse(prog)
:(1 + 1)

julia> typeof(ex1)
Expr
```

Les objets `Expr` contiennent deux parties :

  * un [`Symbol`](@ref) identifiant le type d'expression. Un symbole est un [interned string](https://en.wikipedia.org/wiki/String_interning) identifiant (plus de discussion ci-dessous).

```jldoctest prog
julia> ex1.head
:call
```

  * les arguments d'expression, qui peuvent être des symboles, d'autres expressions ou des valeurs littérales :

```jldoctest prog
julia> ex1.args
3-element Vector{Any}:
  :+
 1
 1
```

Les expressions peuvent également être construites directement dans [prefix notation](https://en.wikipedia.org/wiki/Polish_notation) :

```jldoctest prog
julia> ex2 = Expr(:call, :+, 1, 1)
:(1 + 1)
```

Les deux expressions construites ci-dessus – par analyse et par construction directe – sont équivalentes :

```jldoctest prog
julia> ex1 == ex2
true
```

**Le point clé ici est que le code Julia est représenté en interne comme une structure de données qui est accessible depuis le langage lui-même.**

La fonction [`dump`](@ref) fournit un affichage indenté et annoté des objets `Expr` :

```jldoctest prog
julia> dump(ex2)
Expr
  head: Symbol call
  args: Array{Any}((3,))
    1: Symbol +
    2: Int64 1
    3: Int64 1
```

Les objets `Expr` peuvent également être imbriqués :

```jldoctest ex3
julia> ex3 = Meta.parse("(4 + 4) / 2")
:((4 + 4) / 2)
```

Une autre façon de voir les expressions est avec `Meta.show_sexpr`, qui affiche la forme [S-expression](https://en.wikipedia.org/wiki/S-expression) d'un `Expr` donné, qui peut sembler très familière aux utilisateurs de Lisp. Voici un exemple illustrant l'affichage sur un `Expr` imbriqué :

```jldoctest ex3
julia> Meta.show_sexpr(ex3)
(:call, :/, (:call, :+, 4, 4), 2)
```

### Symbols

Le caractère `:` a deux usages syntaxiques en Julia. La première forme crée un [`Symbol`](@ref), un [interned string](https://en.wikipedia.org/wiki/String_interning) utilisé comme un des éléments de base des expressions, à partir d'identifiants valides :

```jldoctest
julia> s = :foo
:foo

julia> typeof(s)
Symbol
```

Le constructeur [`Symbol`](@ref) prend un nombre quelconque d'arguments et crée un nouveau symbole en concaténant leurs représentations sous forme de chaîne ensemble :

```jldoctest
julia> :foo === Symbol("foo")
true

julia> Symbol("1foo") # `:1foo` would not work, as `1foo` is not a valid identifier
Symbol("1foo")

julia> Symbol("func",10)
:func10

julia> Symbol(:var,'_',"sym")
:var_sym
```

Dans le contexte d'une expression, des symboles sont utilisés pour indiquer l'accès aux variables ; lorsqu'une expression est évaluée, un symbole est remplacé par la valeur liée à ce symbole dans le [scope](@ref scope-of-variables).

Parfois, des parenthèses supplémentaires autour de l'argument de `:` sont nécessaires pour éviter toute ambiguïté dans l'analyse :

```jldoctest
julia> :(:)
:(:)

julia> :(::)
:(::)
```

## Expressions and evaluation

### Quoting

Le deuxième but syntaxique du caractère `:` est de créer des objets d'expression sans utiliser le constructeur explicite [`Expr`](@ref). Cela est appelé *citation*. Le caractère `:`, suivi de parenthèses appariées autour d'une seule instruction de code Julia, produit un objet `Expr` basé sur le code contenu. Voici un exemple de la forme courte utilisée pour citer une expression arithmétique :

```jldoctest
julia> ex = :(a+b*c+1)
:(a + b * c + 1)

julia> typeof(ex)
Expr
```

(pour voir la structure de cette expression, essayez `ex.head` et `ex.args`, ou utilisez [`dump`](@ref) comme ci-dessus ou [`Meta.@dump`](@ref))

Notez que des expressions équivalentes peuvent être construites en utilisant [`Meta.parse`](@ref) ou la forme directe `Expr` :

```jldoctest
julia>      :(a + b*c + 1)       ==
       Meta.parse("a + b*c + 1") ==
       Expr(:call, :+, :a, Expr(:call, :*, :b, :c), 1)
true
```

Les expressions fournies par le parseur ont généralement uniquement des symboles, d'autres expressions et des valeurs littérales comme arguments, tandis que les expressions construites par le code Julia peuvent avoir des valeurs d'exécution arbitraires sans formes littérales comme arguments. Dans cet exemple spécifique, `+` et `a` sont des symboles, `*(b,c)` est une sous-expression, et `1` est un entier signé 64 bits littéral.

Il existe une deuxième forme syntaxique de citation pour plusieurs expressions : des blocs de code entourés de `quote ... end`.

```jldoctest
julia> ex = quote
           x = 1
           y = 2
           x + y
       end
quote
    #= none:2 =#
    x = 1
    #= none:3 =#
    y = 2
    #= none:4 =#
    x + y
end

julia> typeof(ex)
Expr
```

### [Interpolation](@id man-expression-interpolation)

La construction directe d'objets [`Expr`](@ref) avec des arguments de valeur est puissante, mais les constructeurs `Expr` peuvent être fastidieux par rapport à la syntaxe "normale" de Julia. En alternative, Julia permet l'*interpolation* de littéraux ou d'expressions dans des expressions citées. L'interpolation est indiquée par un préfixe `$`.

Dans cet exemple, la valeur de la variable `a` est interpolée :

```jldoctest interp1
julia> a = 1;

julia> ex = :($a + b)
:(1 + b)
```

L'interpolation dans une expression non citée n'est pas supportée et entraînera une erreur de compilation :

```jldoctest interp1
julia> $a + b
ERROR: syntax: "$" expression outside quote
```

Dans cet exemple, le tuple `(1,2,3)` est interpolé en tant qu'expression dans un test conditionnel :

```jldoctest interp1
julia> ex = :(a in $:((1,2,3)) )
:(a in (1, 2, 3))
```

L'utilisation de `$` pour l'interpolation d'expressions rappelle intentionnellement [string interpolation](@ref string-interpolation) et [command interpolation](@ref command-interpolation). L'interpolation d'expressions permet une construction programmatique pratique et lisible d'expressions Julia complexes.

### Splatting interpolation

Remarquez que la syntaxe d'interpolation `$` permet d'insérer uniquement une seule expression dans une expression englobante. Parfois, vous avez un tableau d'expressions et vous avez besoin qu'elles deviennent toutes des arguments de l'expression environnante. Cela peut être fait avec la syntaxe `$(xs...)`. Par exemple, le code suivant génère un appel de fonction où le nombre d'arguments est déterminé de manière programmatique :

```jldoctest interp1
julia> args = [:x, :y, :z];

julia> :(f(1, $(args...)))
:(f(1, x, y, z))
```

### Nested quote

Naturellement, il est possible que des expressions de citation contiennent d'autres expressions de citation. Comprendre comment l'interpolation fonctionne dans ces cas peut être un peu délicat. Considérons cet exemple :

```jldoctest interp1
julia> x = :(1 + 2);

julia> e = quote quote $x end end
quote
    #= none:1 =#
    $(Expr(:quote, quote
    #= none:1 =#
    $(Expr(:$, :x))
end))
end
```

Remarquez que le résultat contient `$x`, ce qui signifie que `x` n'a pas encore été évalué. En d'autres termes, l'expression `$` "appartient" à l'expression de citation intérieure, et donc son argument n'est évalué que lorsque l'expression de citation intérieure est :

```jldoctest interp1
julia> eval(e)
quote
    #= none:1 =#
    1 + 2
end
```

Cependant, l'expression `quote` externe est capable d'interpoler des valeurs à l'intérieur du `$` dans la citation interne. Cela se fait avec plusieurs `$` :

```jldoctest interp1
julia> e = quote quote $$x end end
quote
    #= none:1 =#
    $(Expr(:quote, quote
    #= none:1 =#
    $(Expr(:$, :(1 + 2)))
end))
end
```

Remarquez que `(1 + 2)` apparaît maintenant dans le résultat au lieu du symbole `x`. L'évaluation de cette expression donne un `3` interpolé :

```jldoctest interp1
julia> eval(e)
quote
    #= none:1 =#
    3
end
```

L'intuition derrière ce comportement est que `x` est évalué une fois pour chaque `$` : un `$` fonctionne de manière similaire à `eval(:x)`, donnant la valeur de `x`, tandis que deux `$` font l'équivalent de `eval(eval(:x))`.

### [QuoteNode](@id man-quote-node)

The usual representation of a `quote` form in an AST is an [`Expr`](@ref) with head `:quote`:

```jldoctest interp1
julia> dump(Meta.parse(":(1+2)"))
Expr
  head: Symbol quote
  args: Array{Any}((1,))
    1: Expr
      head: Symbol call
      args: Array{Any}((3,))
        1: Symbol +
        2: Int64 1
        3: Int64 2
```

Comme nous l'avons vu, de telles expressions prennent en charge l'interpolation avec `$`. Cependant, dans certaines situations, il est nécessaire de citer du code *sans* effectuer d'interpolation. Ce type de citation n'a pas encore de syntaxe, mais est représenté en interne comme un objet de type `QuoteNode` :

```jldoctest interp1
julia> eval(Meta.quot(Expr(:$, :(1+2))))
3

julia> eval(QuoteNode(Expr(:$, :(1+2))))
:($(Expr(:$, :(1 + 2))))
```

Le parseur produit des `QuoteNode`s pour des éléments cités simples comme des symboles :

```jldoctest interp1
julia> dump(Meta.parse(":x"))
QuoteNode
  value: Symbol x
```

`QuoteNode` peut également être utilisé pour certaines tâches avancées de métaprogrammation.

### Evaluating expressions

Étant donné un objet d'expression, on peut amener Julia à évaluer (exécuter) celui-ci au niveau global en utilisant [`eval`](@ref) :

```jldoctest interp1
julia> ex1 = :(1 + 2)
:(1 + 2)

julia> eval(ex1)
3

julia> ex = :(a + b)
:(a + b)

julia> eval(ex)
ERROR: UndefVarError: `b` not defined in `Main`
[...]

julia> a = 1; b = 2;

julia> eval(ex)
3
```

Chaque [module](@ref modules) a sa propre fonction [`eval`](@ref) qui évalue des expressions dans son espace global. Les expressions passées à `4d61726b646f776e2e436f64652822222c20226576616c2229_40726566` ne se limitent pas à retourner des valeurs – elles peuvent également avoir des effets secondaires qui modifient l'état de l'environnement du module englobant :

```jldoctest
julia> ex = :(x = 1)
:(x = 1)

julia> x
ERROR: UndefVarError: `x` not defined in `Main`

julia> eval(ex)
1

julia> x
1
```

Ici, l'évaluation d'un objet d'expression entraîne l'attribution d'une valeur à la variable globale `x`.

Puisque les expressions ne sont que des objets `Expr` qui peuvent être construits de manière programmatique puis évalués, il est possible de générer dynamiquement du code arbitraire qui peut ensuite être exécuté en utilisant [`eval`](@ref). Voici un exemple simple :

```julia-repl
julia> a = 1;

julia> ex = Expr(:call, :+, a, :b)
:(1 + b)

julia> a = 0; b = 2;

julia> eval(ex)
3
```

La valeur de `a` est utilisée pour construire l'expression `ex` qui applique la fonction `+` à la valeur 1 et à la variable `b`. Notez la distinction importante entre la façon dont `a` et `b` sont utilisés :

  * La valeur de la *variable* `a` au moment de la construction de l'expression est utilisée comme une valeur immédiate dans l'expression. Ainsi, la valeur de `a` lorsque l'expression est évaluée n'a plus d'importance : la valeur dans l'expression est déjà `1`, indépendamment de la valeur que pourrait avoir `a`.
  * D'autre part, le *symbole* `:b` est utilisé dans la construction d'expressions, donc la valeur de la variable `b` à ce moment-là est sans importance – `:b` est juste un symbole et la variable `b` n'a même pas besoin d'être définie. Cependant, au moment de l'évaluation de l'expression, la valeur du symbole `:b` est résolue en recherchant la valeur de la variable `b`.

### Functions on `Expr`essions

As hinted above, one extremely useful feature of Julia is the capability to generate and manipulate Julia code within Julia itself. We have already seen one example of a function returning [`Expr`](@ref) objects: the [`Meta.parse`](@ref) function, which takes a string of Julia code and returns the corresponding `Expr`. A function can also take one or more `Expr` objects as arguments, and return another `Expr`. Here is a simple, motivating example:

```jldoctest
julia> function math_expr(op, op1, op2)
           expr = Expr(:call, op, op1, op2)
           return expr
       end
math_expr (generic function with 1 method)

julia>  ex = math_expr(:+, 1, Expr(:call, :*, 4, 5))
:(1 + 4 * 5)

julia> eval(ex)
21
```

En voici un autre exemple, voici une fonction qui double tout argument numérique, mais laisse les expressions intactes :

```jldoctest
julia> function make_expr2(op, opr1, opr2)
           opr1f, opr2f = map(x -> isa(x, Number) ? 2*x : x, (opr1, opr2))
           retexpr = Expr(:call, op, opr1f, opr2f)
           return retexpr
       end
make_expr2 (generic function with 1 method)

julia> make_expr2(:+, 1, 2)
:(2 + 4)

julia> ex = make_expr2(:+, 1, Expr(:call, :*, 5, 8))
:(2 + 5 * 8)

julia> eval(ex)
42
```

## [Macros](@id man-macros)

Les macros fournissent un mécanisme pour inclure du code généré dans le corps final d'un programme. Une macro associe un tuple d'arguments à une *expression* retournée, et l'expression résultante est compilée directement plutôt que de nécessiter un appel [`eval`](@ref) à l'exécution. Les arguments de la macro peuvent inclure des expressions, des valeurs littérales et des symboles.

### Basics

Voici un macro extraordinairement simple :

```jldoctest sayhello
julia> macro sayhello()
           return :( println("Hello, world!") )
       end
@sayhello (macro with 1 method)
```

Les macros ont un caractère dédié dans la syntaxe de Julia : le `@` (signe @), suivi du nom unique déclaré dans un bloc `macro NAME ... end`. Dans cet exemple, le compilateur remplacera toutes les instances de `@sayhello` par :

```julia
:( println("Hello, world!") )
```

Lorsque `@sayhello` est saisi dans le REPL, l'expression s'exécute immédiatement, nous ne voyons donc que le résultat de l'évaluation :

```jldoctest sayhello
julia> @sayhello()
Hello, world!
```

Maintenant, considérons un macro légèrement plus complexe :

```jldoctest sayhello2
julia> macro sayhello(name)
           return :( println("Hello, ", $name) )
       end
@sayhello (macro with 1 method)
```

Ce macro prend un argument : `name`. Lorsque `@sayhello` est rencontré, l'expression citée est *développée* pour interpoler la valeur de l'argument dans l'expression finale :

```jldoctest sayhello2
julia> @sayhello("human")
Hello, human
```

Nous pouvons voir l'expression de retour citée en utilisant la fonction [`macroexpand`](@ref) (**note importante :** c'est un outil extrêmement utile pour le débogage des macros) :

```julia-repl sayhello2
julia> ex = macroexpand(Main, :(@sayhello("human")) )
:(Main.println("Hello, ", "human"))

julia> typeof(ex)
Expr
```

Nous pouvons voir que le littéral `"human"` a été interpolé dans l'expression.

Il existe également un macro [`@macroexpand`](@ref) qui est peut-être un peu plus pratique que la fonction `macroexpand` :

```jldoctest sayhello2
julia> @macroexpand @sayhello "human"
:(println("Hello, ", "human"))
```

### Hold up: why macros?

Nous avons déjà vu une fonction `f(::Expr...) -> Expr` dans une section précédente. En fait, [`macroexpand`](@ref) est également une telle fonction. Alors, pourquoi les macros existent-elles ?

Les macros sont nécessaires car elles s'exécutent lorsque le code est analysé, permettant ainsi au programmeur de générer et d'inclure des fragments de code personnalisé *avant* que le programme complet ne soit exécuté. Pour illustrer la différence, considérons l'exemple suivant :

```julia-repl whymacros
julia> macro twostep(arg)
           println("I execute at parse time. The argument is: ", arg)
           return :(println("I execute at runtime. The argument is: ", $arg))
       end
@twostep (macro with 1 method)

julia> ex = macroexpand(Main, :(@twostep :(1, 2, 3)) );
I execute at parse time. The argument is: :((1, 2, 3))
```

L'appel initial à [`println`](@ref) est exécuté lorsque [`macroexpand`](@ref) est appelé. L'expression résultante contient *uniquement* le second `println` :

```julia-repl whymacros
julia> typeof(ex)
Expr

julia> ex
:(println("I execute at runtime. The argument is: ", $(Expr(:copyast, :($(QuoteNode(:((1, 2, 3)))))))))

julia> eval(ex)
I execute at runtime. The argument is: (1, 2, 3)
```

### Macro invocation

Les macros sont invoquées avec la syntaxe générale suivante :

```julia
@name expr1 expr2 ...
@name(expr1, expr2, ...)
```

Notez le `@` distinct avant le nom de la macro et l'absence de virgules entre les expressions d'argument dans la première forme, ainsi que l'absence d'espace après `@name` dans la deuxième forme. Les deux styles ne doivent pas être mélangés. Par exemple, la syntaxe suivante est différente des exemples ci-dessus ; elle passe le tuple `(expr1, expr2, ...)` comme un seul argument à la macro :

```julia
@name (expr1, expr2, ...)
```

Une autre façon d'invoquer une macro sur un littéral de tableau (ou une compréhension) est de juxtaposer les deux sans utiliser de parenthèses. Dans ce cas, le tableau sera la seule expression transmise à la macro. La syntaxe suivante est équivalente (et différente de `@name [a b] * v`) :

```julia
@name[a b] * v
@name([a b]) * v
```

Il est important de souligner que les macros reçoivent leurs arguments sous forme d'expressions, de littéraux ou de symboles. Une façon d'explorer les arguments des macros est d'appeler la fonction [`show`](@ref) dans le corps de la macro :

```jldoctest
julia> macro showarg(x)
           show(x)
           # ... remainder of macro, returning an expression
       end
@showarg (macro with 1 method)

julia> @showarg(a)
:a

julia> @showarg(1+1)
:(1 + 1)

julia> @showarg(println("Yo!"))
:(println("Yo!"))

julia> @showarg(1)        # Numeric literal
1

julia> @showarg("Yo!")    # String literal
"Yo!"

julia> @showarg("Yo! $("hello")")    # String with interpolation is an Expr rather than a String
:("Yo! $("hello")")
```

En plus de la liste d'arguments donnée, chaque macro reçoit des arguments supplémentaires nommés `__source__` et `__module__`.

L'argument `__source__` fournit des informations (sous la forme d'un objet `LineNumberNode`) sur l'emplacement du parseur du signe `@` à partir de l'invocation de la macro. Cela permet aux macros d'inclure de meilleures informations de diagnostic d'erreur, et est couramment utilisé par les macros de journalisation, de parsing de chaînes, et de documentation, par exemple, ainsi que pour implémenter les macros [`@__LINE__`](@ref), [`@__FILE__`](@ref), et [`@__DIR__`](@ref).

Les informations de localisation peuvent être consultées en se référant à `__source__.line` et `__source__.file` :

```jldoctest
julia> macro __LOCATION__(); return QuoteNode(__source__); end
@__LOCATION__ (macro with 1 method)

julia> dump(
            @__LOCATION__(
       ))
LineNumberNode
  line: Int64 2
  file: Symbol none
```

L'argument `__module__` fournit des informations (sous la forme d'un objet `Module`) sur le contexte d'expansion de l'invocation de la macro. Cela permet aux macros de rechercher des informations contextuelles, telles que des liaisons existantes, ou d'insérer la valeur en tant qu'argument supplémentaire dans un appel de fonction à l'exécution effectuant une auto-réflexion dans le module actuel.

### Building an advanced macro

Voici une définition simplifiée de la macro [`@assert`](@ref) de Julia :

```jldoctest building
julia> macro assert(ex)
           return :( $ex ? nothing : throw(AssertionError($(string(ex)))) )
       end
@assert (macro with 1 method)
```

Ce macro peut être utilisé comme ceci :

```jldoctest building
julia> @assert 1 == 1.0

julia> @assert 1 == 0
ERROR: AssertionError: 1 == 0
```

À la place de la syntaxe écrite, l'appel de macro est développé au moment de l'analyse en son résultat retourné. Cela équivaut à écrire :

```julia
1 == 1.0 ? nothing : throw(AssertionError("1 == 1.0"))
1 == 0 ? nothing : throw(AssertionError("1 == 0"))
```

C'est-à-dire que, lors du premier appel, l'expression `:(1 == 1.0)` est insérée dans l'emplacement de la condition de test, tandis que la valeur de `string(:(1 == 1.0))` est insérée dans l'emplacement du message d'assertion. L'ensemble de l'expression, ainsi construite, est placé dans l'arbre syntaxique où se produit l'appel de la macro `@assert`. Ensuite, au moment de l'exécution, si l'expression de test évalue à vrai, alors [`nothing`](@ref) est retourné, tandis que si le test est faux, une erreur est levée indiquant l'expression affirmée qui était fausse. Remarquez qu'il ne serait pas possible d'écrire cela comme une fonction, car seule la *valeur* de la condition est disponible et il serait impossible d'afficher l'expression qui l'a calculée dans le message d'erreur.

La définition réelle de `@assert` dans Julia Base est plus compliquée. Elle permet à l'utilisateur de spécifier optionnellement son propre message d'erreur, au lieu de simplement imprimer l'expression échouée. Tout comme dans les fonctions avec un nombre variable d'arguments ([Varargs Functions](@ref)), cela est spécifié avec des points de suspension suivant le dernier argument :

```jldoctest assert2
julia> macro assert(ex, msgs...)
           msg_body = isempty(msgs) ? ex : msgs[1]
           msg = string(msg_body)
           return :($ex ? nothing : throw(AssertionError($msg)))
       end
@assert (macro with 1 method)
```

Maintenant, `@assert` a deux modes de fonctionnement, selon le nombre d'arguments qu'il reçoit ! S'il n'y a qu'un seul argument, le tuple d'expressions capturé par `msgs` sera vide et il se comportera de la même manière que la définition plus simple ci-dessus. Mais maintenant, si l'utilisateur spécifie un deuxième argument, il est imprimé dans le corps du message au lieu de l'expression échouée. Vous pouvez inspecter le résultat d'une expansion de macro avec la macro judicieusement nommée [`@macroexpand`](@ref) :

```julia-repl assert2
julia> @macroexpand @assert a == b
:(if Main.a == Main.b
        Main.nothing
    else
        Main.throw(Main.AssertionError("a == b"))
    end)

julia> @macroexpand @assert a==b "a should equal b!"
:(if Main.a == Main.b
        Main.nothing
    else
        Main.throw(Main.AssertionError("a should equal b!"))
    end)
```

Il y a encore un autre cas que le macro `@assert` gère : que se passe-t-il, en plus d'imprimer "a devrait être égal à b", si nous voulions imprimer leurs valeurs ? On pourrait naïvement essayer d'utiliser l'interpolation de chaînes dans le message personnalisé, par exemple, `@assert a==b "a ($a) devrait être égal à b ($b)!"`, mais cela ne fonctionnera pas comme prévu avec le macro ci-dessus. Pouvez-vous voir pourquoi ? Rappelez-vous de [string interpolation](@ref string-interpolation) que une chaîne interpolée est réécrite en un appel à [`string`](@ref). Comparez :

```jldoctest
julia> typeof(:("a should equal b"))
String

julia> typeof(:("a ($a) should equal b ($b)!"))
Expr

julia> dump(:("a ($a) should equal b ($b)!"))
Expr
  head: Symbol string
  args: Array{Any}((5,))
    1: String "a ("
    2: Symbol a
    3: String ") should equal b ("
    4: Symbol b
    5: String ")!"
```

Alors maintenant, au lieu d'obtenir une chaîne simple dans `msg_body`, la macro reçoit une expression complète qui devra être évaluée pour s'afficher comme prévu. Cela peut être directement intégré dans l'expression retournée en tant qu'argument de l'appel [`string`](@ref) ; voir [`error.jl`](https://github.com/JuliaLang/julia/blob/master/base/error.jl) pour l'implémentation complète.

Le macro `@assert` utilise de manière efficace l'insertion dans des expressions citées pour simplifier la manipulation des expressions à l'intérieur du corps du macro.

### Hygiene

Un problème qui se pose dans des macros plus complexes est celui de [hygiene](https://en.wikipedia.org/wiki/Hygienic_macro). En résumé, les macros doivent s'assurer que les variables qu'elles introduisent dans leurs expressions retournées ne se heurtent pas accidentellement aux variables existantes dans le code environnant dans lequel elles s'étendent. Inversement, les expressions qui sont passées à une macro en tant qu'arguments sont souvent *attendues* pour être évaluées dans le contexte du code environnant, interagissant avec et modifiant les variables existantes. Une autre préoccupation découle du fait qu'une macro peut être appelée dans un module différent de celui où elle a été définie. Dans ce cas, nous devons nous assurer que toutes les variables globales sont résolues au bon module. Julia a déjà un avantage majeur par rapport aux langages avec une expansion de macro textuelle (comme C) en ce sens qu'elle n'a besoin de considérer que l'expression retournée. Toutes les autres variables (comme `msg` dans `@assert` ci-dessus) suivent le [normal scoping block behavior](@ref scope-of-variables).

Pour démontrer ces problèmes, considérons l'écriture d'un macro `@time` qui prend une expression comme argument, enregistre le temps, évalue l'expression, enregistre à nouveau le temps, imprime la différence entre les temps avant et après, puis a la valeur de l'expression comme valeur finale. Le macro pourrait ressembler à ceci :

```julia
macro time(ex)
    return quote
        local t0 = time_ns()
        local val = $ex
        local t1 = time_ns()
        println("elapsed time: ", (t1-t0)/1e9, " seconds")
        val
    end
end
```

Ici, nous voulons que `t0`, `t1` et `val` soient des variables temporaires privées, et nous voulons que `time_ns` fasse référence à la fonction [`time_ns`](@ref) dans Julia Base, et non à une variable `time_ns` que l'utilisateur pourrait avoir (il en va de même pour `println`). Imaginez les problèmes qui pourraient survenir si l'expression utilisateur `ex` contenait également des affectations à une variable appelée `t0`, ou définissait sa propre variable `time_ns`. Nous pourrions obtenir des erreurs ou un comportement mystérieusement incorrect.

L'expandeur de macro de Julia résout ces problèmes de la manière suivante. Tout d'abord, les variables au sein d'un résultat de macro sont classées comme locales ou globales. Une variable est considérée comme locale si elle est assignée (et non déclarée globale), déclarée locale, ou utilisée comme nom d'argument de fonction. Sinon, elle est considérée comme globale. Les variables locales sont ensuite renommées pour être uniques (en utilisant la fonction [`gensym`](@ref), qui génère de nouveaux symboles), et les variables globales sont résolues dans l'environnement de définition de la macro. Par conséquent, les deux préoccupations ci-dessus sont traitées ; les variables locales de la macro ne seront pas en conflit avec les variables utilisateur, et `time_ns` et `println` se référeront aux définitions de Julia Base.

Un problème demeure cependant. Considérez l'utilisation suivante de cette macro :

```julia
module MyModule
import Base.@time

time_ns() = ... # compute something

@time time_ns()
end
```

Ici, l'expression utilisateur `ex` est un appel à `time_ns`, mais ce n'est pas la même fonction `time_ns` que celle utilisée par la macro. Elle fait clairement référence à `MyModule.time_ns`. Par conséquent, nous devons veiller à ce que le code dans `ex` soit résolu dans l'environnement d'appel de la macro. Cela se fait en "échappant" l'expression avec [`esc`](@ref) :

```julia
macro time(ex)
    ...
    local val = $(esc(ex))
    ...
end
```

Une expression enveloppée de cette manière est laissée intacte par l'expanseur de macro et est simplement collée dans la sortie telle quelle. Par conséquent, elle sera résolue dans l'environnement d'appel de la macro.

Ce mécanisme d'échappement peut être utilisé pour "violer" l'hygiène lorsque cela est nécessaire, afin d'introduire ou de manipuler des variables utilisateur. Par exemple, le macro suivant définit `x` à zéro dans l'environnement d'appel :

```jldoctest
julia> macro zerox()
           return esc(:(x = 0))
       end
@zerox (macro with 1 method)

julia> function foo()
           x = 1
           @zerox
           return x # is zero
       end
foo (generic function with 1 method)

julia> foo()
0
```

Ce type de manipulation des variables doit être utilisé avec prudence, mais est parfois très pratique.

Obtenir les règles d'hygiène correctes peut être un défi redoutable. Avant d'utiliser un macro, vous voudrez peut-être considérer si une fermeture de fonction serait suffisante. Une autre stratégie utile consiste à différer autant de travail que possible à l'exécution. Par exemple, de nombreux macros enveloppent simplement leurs arguments dans un `QuoteNode` ou un autre [`Expr`](@ref) similaire. Quelques exemples incluent `@task body` qui retourne simplement `schedule(Task(() -> $body))`, et `@eval expr`, qui retourne simplement `eval(QuoteNode(expr))`.

Pour démontrer, nous pourrions réécrire l'exemple `@time` ci-dessus comme suit :

```julia
macro time(expr)
    return :(timeit(() -> $(esc(expr))))
end
function timeit(f)
    t0 = time_ns()
    val = f()
    t1 = time_ns()
    println("elapsed time: ", (t1-t0)/1e9, " seconds")
    return val
end
```

Cependant, nous ne faisons pas cela pour une bonne raison : envelopper l'`expr` dans un nouveau bloc de portée (la fonction anonyme) change également légèrement le sens de l'expression (la portée de toutes les variables qu'elle contient), alors que nous voulons que `@time` soit utilisable avec un impact minimal sur le code enveloppé.

### Macros and dispatch

Les macros, tout comme les fonctions Julia, sont génériques. Cela signifie qu'elles peuvent également avoir plusieurs définitions de méthode, grâce au dispatch multiple :

```jldoctest macromethods
julia> macro m end
@m (macro with 0 methods)

julia> macro m(args...)
           println("$(length(args)) arguments")
       end
@m (macro with 1 method)

julia> macro m(x,y)
           println("Two arguments")
       end
@m (macro with 2 methods)

julia> @m "asd"
1 arguments

julia> @m 1 2
Two arguments
```

Cependant, il faut garder à l'esprit que le dispatching macro est basé sur les types d'AST qui sont remis à la macro, et non sur les types que l'AST évalue à l'exécution :

```jldoctest macromethods
julia> macro m(::Int)
           println("An Integer")
       end
@m (macro with 3 methods)

julia> @m 2
An Integer

julia> x = 2
2

julia> @m x
1 arguments
```

## Code Generation

Lorsqu'une quantité significative de code répétitif standard est requise, il est courant de le générer de manière programmatique pour éviter la redondance. Dans la plupart des langages, cela nécessite une étape de construction supplémentaire et un programme séparé pour générer le code répétitif. En Julia, l'interpolation d'expressions et [`eval`](@ref) permettent à cette génération de code de se produire dans le cours normal de l'exécution du programme. Par exemple, considérons le type personnalisé suivant.

```jldoctest mynumber-codegen
struct MyNumber
    x::Float64
end
# output

```

pour lequel nous souhaitons ajouter un certain nombre de méthodes. Nous pouvons le faire de manière programmatique dans la boucle suivante :

```jldoctest mynumber-codegen
for op = (:sin, :cos, :tan, :log, :exp)
    eval(quote
        Base.$op(a::MyNumber) = MyNumber($op(a.x))
    end)
end
# output

```

et nous pouvons maintenant utiliser ces fonctions avec notre type personnalisé :

```jldoctest mynumber-codegen
julia> x = MyNumber(π)
MyNumber(3.141592653589793)

julia> sin(x)
MyNumber(1.2246467991473532e-16)

julia> cos(x)
MyNumber(-1.0)
```

De cette manière, Julia agit comme son propre [preprocessor](https://en.wikipedia.org/wiki/Preprocessor), et permet la génération de code depuis l'intérieur du langage. Le code ci-dessus pourrait être écrit de manière légèrement plus concise en utilisant la forme de citation avec le préfixe `:` :

```julia
for op = (:sin, :cos, :tan, :log, :exp)
    eval(:(Base.$op(a::MyNumber) = MyNumber($op(a.x))))
end
```

Ce type de génération de code en langage, cependant, utilisant le modèle `eval(quote(...))`, est suffisamment courant pour que Julia soit livrée avec un macro pour abréger ce modèle :

```julia
for op = (:sin, :cos, :tan, :log, :exp)
    @eval Base.$op(a::MyNumber) = MyNumber($op(a.x))
end
```

Le macro [`@eval`](@ref) réécrit cet appel pour être précisément équivalent aux versions plus longues ci-dessus. Pour des blocs plus longs de code généré, l'argument d'expression donné à `4d61726b646f776e2e436f64652822222c2022406576616c2229_40726566` peut être un bloc :

```julia
@eval begin
    # multiple lines
end
```

## [Non-Standard String Literals](@id meta-non-standard-string-literals)

Rappelez-vous de [Strings](@ref non-standard-string-literals) que les littéraux de chaîne préfixés par un identifiant sont appelés littéraux de chaîne non standard, et peuvent avoir des sémantiques différentes de celles des littéraux de chaîne non préfixés. Par exemple :

  * `r"^\s*(?:#|$)"` produit un [regular expression object](@ref man-regex-literals) plutôt qu'une chaîne.
  * `b"DATA\xff\u2200"` est un [byte array literal](@ref man-byte-array-literals) pour `[68,65,84,65,255,226,136,128]`.

Peut-être de manière surprenante, ces comportements ne sont pas codés en dur dans le parseur ou le compilateur Julia. Au lieu de cela, ce sont des comportements personnalisés fournis par un mécanisme général que tout le monde peut utiliser : les littéraux de chaîne préfixés sont analysés comme des appels à des macros nommées de manière spéciale. Par exemple, la macro d'expression régulière est simplement la suivante :

```julia
macro r_str(p)
    Regex(p)
end
```

C'est tout. Cette macro indique que le contenu littéral de la chaîne littérale `r"^\s*(?:#|$)"` doit être passé à la macro `@r_str` et que le résultat de cette expansion doit être placé dans l'arbre syntaxique à l'endroit où la chaîne littérale se trouve. En d'autres termes, l'expression `r"^\s*(?:#|$)"` est équivalente à placer directement l'objet suivant dans l'arbre syntaxique :

```julia
Regex("^\\s*(?:#|\$)")
```

Non seulement la forme littérale de chaîne est plus courte et beaucoup plus pratique, mais elle est également plus efficace : puisque l'expression régulière est compilée et que l'objet `Regex` est en fait créé *lorsque le code est compilé*, la compilation n'a lieu qu'une seule fois, plutôt qu'à chaque fois que le code est exécuté. Considérez si l'expression régulière se trouve dans une boucle :

```julia
for line = lines
    m = match(r"^\s*(?:#|$)", line)
    if m === nothing
        # non-comment
    else
        # comment
    end
end
```

Puisque l'expression régulière `r"^\s*(?:#|$)"` est compilée et insérée dans l'arbre de syntaxe lorsque ce code est analysé, l'expression n'est compilée qu'une seule fois au lieu de chaque fois que la boucle est exécutée. Pour accomplir cela sans macros, il faudrait écrire cette boucle comme ceci :

```julia
re = Regex("^\\s*(?:#|\$)")
for line = lines
    m = match(re, line)
    if m === nothing
        # non-comment
    else
        # comment
    end
end
```

De plus, si le compilateur ne pouvait pas déterminer que l'objet regex était constant sur toutes les boucles, certaines optimisations pourraient ne pas être possibles, rendant cette version encore moins efficace que la forme littérale plus pratique ci-dessus. Bien sûr, il existe encore des situations où la forme non littérale est plus pratique : si l'on doit interpoler une variable dans l'expression régulière, il faut adopter cette approche plus verbeuse ; dans les cas où le motif de l'expression régulière lui-même est dynamique, changeant potentiellement à chaque itération de boucle, un nouvel objet d'expression régulière doit être construit à chaque itération. Dans la grande majorité des cas d'utilisation, cependant, les expressions régulières ne sont pas construites sur la base de données d'exécution. Dans cette majorité de cas, la possibilité d'écrire des expressions régulières en tant que valeurs de temps de compilation est inestimable.

Le mécanisme des littéraux de chaîne définis par l'utilisateur est profondément, puissamment efficace. Non seulement les littéraux non standards de Julia sont implémentés en utilisant cela, mais la syntaxe des littéraux de commande (``` `echo "Hello, $person"` ```) est également implémentée à l'aide de la macro apparemment inoffensive suivante :

```julia
macro cmd(str)
    :(cmd_gen($(shell_parse(str)[1])))
end
```

Bien sûr, une grande partie de la complexité est cachée dans les fonctions utilisées dans cette définition de macro, mais ce ne sont que des fonctions, écrites entièrement en Julia. Vous pouvez lire leur source et voir précisément ce qu'elles font – et tout ce qu'elles font, c'est construire des objets d'expression à insérer dans l'arbre de syntaxe de votre programme.

Comme les littéraux de chaîne, les littéraux de commande peuvent également être préfixés par un identifiant pour former ce que l'on appelle des littéraux de commande non standard. Ces littéraux de commande sont analysés comme des appels à des macros spécialement nommées. Par exemple, la syntaxe ```custom`literal` ``` est analysée comme `@custom_cmd "literal"`. Julia elle-même ne contient pas de littéraux de commande non standard, mais les packages peuvent utiliser cette syntaxe. Mis à part la syntaxe différente et le suffixe `_cmd` au lieu du suffixe `_str`, les littéraux de commande non standard se comportent exactement comme les littéraux de chaîne non standard.

Dans le cas où deux modules fournissent des littéraux de chaîne ou de commande non standard avec le même nom, il est possible de qualifier le littéral de chaîne ou de commande avec un nom de module. Par exemple, si à la fois `Foo` et `Bar` fournissent le littéral de chaîne non standard `@x_str`, alors on peut écrire `Foo.x"literal"` ou `Bar.x"literal"` pour faire la distinction entre les deux.

Une autre façon de définir une macro serait comme ceci :

```julia
macro foo_str(str, flag)
    # do stuff
end
```

Cette macro peut ensuite être appelée avec la syntaxe suivante :

```julia
foo"str"flag
```

Le type de drapeau dans la syntaxe mentionnée ci-dessus serait une `String` contenant tout ce qui suit le littéral de chaîne.

## Generated functions

Une macro très spéciale est [`@generated`](@ref), qui vous permet de définir ce qu'on appelle des *fonctions générées*. Celles-ci ont la capacité de générer du code spécialisé en fonction des types de leurs arguments avec plus de flexibilité et/ou moins de code que ce qui peut être réalisé avec le dispatch multiple. Alors que les macros fonctionnent avec des expressions au moment de l'analyse et ne peuvent pas accéder aux types de leurs entrées, une fonction générée est développée à un moment où les types des arguments sont connus, mais la fonction n'est pas encore compilée.

Au lieu d'effectuer un calcul ou une action, une déclaration de fonction générée renvoie une expression citée qui forme ensuite le corps de la méthode correspondant aux types des arguments. Lorsqu'une fonction générée est appelée, l'expression qu'elle renvoie est compilée puis exécutée. Pour rendre cela efficace, le résultat est généralement mis en cache. Et pour rendre cela inférable, seul un sous-ensemble limité du langage est utilisable. Ainsi, les fonctions générées offrent un moyen flexible de déplacer le travail du temps d'exécution au temps de compilation, au prix de restrictions plus importantes sur les constructions autorisées.

Lors de la définition des fonctions générées, il y a cinq différences principales par rapport aux fonctions ordinaires :

1. Vous annotez la déclaration de fonction avec le macro `@generated`. Cela ajoute des informations à l'AST qui permettent au compilateur de savoir qu'il s'agit d'une fonction générée.
2. Dans le corps de la fonction générée, vous n'avez accès qu'aux *types* des arguments – pas à leurs valeurs.
3. Au lieu de calculer quelque chose ou d'effectuer une action, vous renvoyez une *expression citée* qui, lorsqu'elle est évaluée, fait ce que vous voulez.
4. Les fonctions générées ne sont autorisées à appeler que des fonctions qui ont été définies *avant* la définition de la fonction générée. (Le non-respect de cette règle peut entraîner des `MethodErrors` faisant référence à des fonctions d'un âge de monde futur.)
5. Les fonctions générées ne doivent pas *muter* ou *observer* un état global non constant (y compris, par exemple, l'E/S, les verrous, les dictionnaires non locaux, ou utiliser [`hasmethod`](@ref)). Cela signifie qu'elles ne peuvent lire que des constantes globales et ne peuvent avoir aucun effet secondaire. En d'autres termes, elles doivent être complètement pures. En raison d'une limitation d'implémentation, cela signifie également qu'elles ne peuvent actuellement pas définir une fermeture ou un générateur.

Il est plus facile d'illustrer cela avec un exemple. Nous pouvons déclarer une fonction générée `foo` comme

```jldoctest generated
julia> @generated function foo(x)
           Core.println(x)
           return :(x * x)
       end
foo (generic function with 1 method)
```

Notez que le corps renvoie une expression citée, à savoir `:(x * x)`, plutôt que simplement la valeur de `x * x`.

Du point de vue de l'appelant, ceci est identique à une fonction régulière ; en fait, vous n'avez pas besoin de savoir si vous appelez une fonction régulière ou générée. Voyons comment `foo` se comporte :

```jldoctest generated
julia> x = foo(2); # note: output is from println() statement in the body
Int64

julia> x           # now we print x
4

julia> y = foo("bar");
String

julia> y
"barbar"
```

Ainsi, nous voyons que dans le corps de la fonction générée, `x` est le *type* de l'argument passé, et la valeur retournée par la fonction générée est le résultat de l'évaluation de l'expression citée que nous avons retournée de la définition, maintenant avec la *valeur* de `x`.

Que se passe-t-il si nous évaluons `foo` à nouveau avec un type que nous avons déjà utilisé ?

```jldoctest generated
julia> foo(4)
16
```

Notez qu'il n'y a pas d'impression de [`Int64`](@ref). Nous pouvons voir que le corps de la fonction générée n'a été exécuté qu'une seule fois ici, pour l'ensemble spécifique des types d'arguments, et le résultat a été mis en cache. Après cela, pour cet exemple, l'expression renvoyée par la fonction générée lors de la première invocation a été réutilisée comme corps de méthode. Cependant, le comportement de mise en cache réel est une optimisation de performance définie par l'implémentation, il est donc invalide de dépendre trop étroitement de ce comportement.

Le nombre de fois qu'une fonction générée est générée *peut* n'être qu'une seule fois, mais il *peut* aussi être plus fréquent, ou sembler ne pas se produire du tout. En conséquence, vous ne devez *jamais* écrire une fonction générée avec des effets de bord - quand et à quelle fréquence les effets de bord se produisent est indéfini. (C'est vrai pour les macros aussi - et tout comme pour les macros, l'utilisation de [`eval`](@ref) dans une fonction générée est un signe que vous faites quelque chose de mal.) Cependant, contrairement aux macros, le système d'exécution ne peut pas gérer correctement un appel à `4d61726b646f776e2e436f64652822222c20226576616c2229_40726566`, donc il est interdit.

Il est également important de voir comment les fonctions `@generated` interagissent avec la redéfinition de méthodes. En suivant le principe qu'une fonction `@generated` correcte ne doit pas observer d'état mutable ni provoquer de mutation de l'état global, nous constatons le comportement suivant. Observez que la fonction générée *ne peut pas* appeler une méthode qui n'a pas été définie avant la *définition* de la fonction générée elle-même.

Initialement, `f(x)` a une seule définition.

```jldoctest redefinition
julia> f(x) = "original definition";
```

Définir d'autres opérations qui utilisent `f(x)` :

```jldoctest redefinition
julia> g(x) = f(x);

julia> @generated gen1(x) = f(x);

julia> @generated gen2(x) = :(f(x));
```

Nous ajoutons maintenant quelques nouvelles définitions pour `f(x)` :

```jldoctest redefinition
julia> f(x::Int) = "definition for Int";

julia> f(x::Type{Int}) = "definition for Type{Int}";
```

et comparez comment ces résultats diffèrent :

```jldoctest redefinition
julia> f(1)
"definition for Int"

julia> g(1)
"definition for Int"

julia> gen1(1)
"original definition"

julia> gen2(1)
"definition for Int"
```

Chaque méthode d'une fonction générée a sa propre vue des fonctions définies :

```jldoctest redefinition
julia> @generated gen1(x::Real) = f(x);

julia> gen1(1)
"definition for Type{Int}"
```

La fonction générée `foo` ci-dessus ne faisait rien qu'une fonction normale `foo(x) = x * x` ne pourrait pas faire (à part imprimer le type lors de la première invocation et entraîner un surcoût plus élevé). Cependant, la puissance d'une fonction générée réside dans sa capacité à calculer différentes expressions citées en fonction des types qui lui sont passés :

```jldoctest
julia> @generated function bar(x)
           if x <: Integer
               return :(x ^ 2)
           else
               return :(x)
           end
       end
bar (generic function with 1 method)

julia> bar(4)
16

julia> bar("baz")
"baz"
```

(bien que bien sûr cet exemple artificiel serait plus facilement mis en œuvre en utilisant le dispatch multiple...)

Abuser cela corrompra le système d'exécution et provoquera un comportement indéfini :

```jldoctest
julia> @generated function baz(x)
           if rand() < .9
               return :(x^2)
           else
               return :("boo!")
           end
       end
baz (generic function with 1 method)
```

Étant donné que le corps de la fonction générée est non déterministe, son comportement, *et le comportement de tout le code suivant* est indéfini.

*Ne copiez pas ces exemples !*

Ces exemples sont, espérons-le, utiles pour illustrer comment fonctionnent les fonctions générées, à la fois dans la définition et au site d'appel ; cependant, *ne les copiez pas*, pour les raisons suivantes :

  * la fonction `foo` a des effets de bord (l'appel à `Core.println`), et il est indéfini exactement quand, à quelle fréquence ou combien de fois ces effets de bord se produiront
  * la fonction `bar` résout un problème qui est mieux résolu avec un dispatch multiple - définir `bar(x) = x` et `bar(x::Integer) = x ^ 2` fera la même chose, mais c'est à la fois plus simple et plus rapide.
  * la fonction `baz` est pathologique

Notez que l'ensemble des opérations qui ne doivent pas être tentées dans une fonction générée est illimité, et le système d'exécution ne peut actuellement détecter qu'un sous-ensemble des opérations invalides. Il existe de nombreuses autres opérations qui corrompront simplement le système d'exécution sans notification, généralement de manière subtile, sans lien évident avec la mauvaise définition. Comme le générateur de fonctions est exécuté pendant l'inférence, il doit respecter toutes les limitations de ce code.

Certain opérations qui ne devraient pas être tentées incluent :

1. Mise en cache des pointeurs natifs.
2. Interagir avec le contenu ou les méthodes de `Core.Compiler` de quelque manière que ce soit.
3. Observer tout état mutable.

      * L'inférence sur la fonction générée peut être exécutée à *tout* moment, y compris pendant que votre code tente d'observer ou de modifier cet état.
4. Prendre des verrous : Le code C que vous appelez peut utiliser des verrous en interne (par exemple, il n'est pas problématique d'appeler `malloc`, même si la plupart des implémentations nécessitent des verrous en interne), mais n'essayez pas de détenir ou d'acquérir des verrous pendant l'exécution du code Julia.
5. Appeler une fonction qui est définie après le corps de la fonction générée. Cette condition est assouplie pour les modules précompilés chargés de manière incrémentielle afin de permettre l'appel de n'importe quelle fonction dans le module.

D'accord, maintenant que nous avons une meilleure compréhension de la façon dont les fonctions générées fonctionnent, utilisons-les pour construire des fonctionnalités plus avancées (et valides)...

### An advanced example

La bibliothèque de base de Julia a une fonction interne `sub2ind` pour calculer un index linéaire dans un tableau n-dimensionnel, basé sur un ensemble d'indices multilinéaires n - en d'autres termes, pour calculer l'index `i` qui peut être utilisé pour indexer un tableau `A` en utilisant `A[i]`, au lieu de `A[x,y,z,...]`. Une implémentation possible est la suivante :

```jldoctest sub2ind
julia> function sub2ind_loop(dims::NTuple{N}, I::Integer...) where N
           ind = I[N] - 1
           for i = N-1:-1:1
               ind = I[i]-1 + dims[i]*ind
           end
           return ind + 1
       end;

julia> sub2ind_loop((3, 5), 1, 2)
4
```

La même chose peut être faite en utilisant la récursion :

```jldoctest
julia> sub2ind_rec(dims::Tuple{}) = 1;

julia> sub2ind_rec(dims::Tuple{}, i1::Integer, I::Integer...) =
           i1 == 1 ? sub2ind_rec(dims, I...) : throw(BoundsError());

julia> sub2ind_rec(dims::Tuple{Integer, Vararg{Integer}}, i1::Integer) = i1;

julia> sub2ind_rec(dims::Tuple{Integer, Vararg{Integer}}, i1::Integer, I::Integer...) =
           i1 + dims[1] * (sub2ind_rec(Base.tail(dims), I...) - 1);

julia> sub2ind_rec((3, 5), 1, 2)
4
```

Les deux implémentations, bien que différentes, font essentiellement la même chose : une boucle d'exécution sur les dimensions du tableau, collectant le décalage dans chaque dimension dans l'index final.

Cependant, toutes les informations dont nous avons besoin pour la boucle sont intégrées dans les informations de type des arguments. Cela permet au compilateur de déplacer l'itération au moment de la compilation et d'éliminer complètement les boucles d'exécution. Nous pouvons utiliser des fonctions générées pour obtenir un effet similaire ; dans le jargon des compilateurs, nous utilisons des fonctions générées pour dérouler manuellement la boucle. Le corps devient presque identique, mais au lieu de calculer l'index linéaire, nous construisons une *expression* qui calcule l'index :

```jldoctest sub2ind_gen
julia> @generated function sub2ind_gen(dims::NTuple{N}, I::Integer...) where N
           ex = :(I[$N] - 1)
           for i = (N - 1):-1:1
               ex = :(I[$i] - 1 + dims[$i] * $ex)
           end
           return :($ex + 1)
       end;

julia> sub2ind_gen((3, 5), 1, 2)
4
```

**Quel code cela va-t-il générer ?**

Une façon simple de le découvrir est d'extraire le corps dans une autre fonction (régulière) :

```jldoctest sub2ind_gen2
julia> function sub2ind_gen_impl(dims::Type{T}, I...) where T <: NTuple{N,Any} where N
           length(I) == N || return :(error("partial indexing is unsupported"))
           ex = :(I[$N] - 1)
           for i = (N - 1):-1:1
               ex = :(I[$i] - 1 + dims[$i] * $ex)
           end
           return :($ex + 1)
       end;

julia> @generated function sub2ind_gen(dims::NTuple{N}, I::Integer...) where N
           return sub2ind_gen_impl(dims, I...)
       end;

julia> sub2ind_gen((3, 5), 1, 2)
4
```

Nous pouvons maintenant exécuter `sub2ind_gen_impl` et examiner l'expression qu'il renvoie :

```jldoctest sub2ind_gen2
julia> sub2ind_gen_impl(Tuple{Int,Int}, Int, Int)
:(((I[1] - 1) + dims[1] * (I[2] - 1)) + 1)
```

Donc, le corps de la méthode qui sera utilisé ici n'inclut pas de boucle du tout - juste l'indexation dans les deux tuples, la multiplication et l'addition/soustraction. Toute la boucle est effectuée à la compilation, et nous évitons complètement les boucles pendant l'exécution. Ainsi, nous ne bouclons *qu'une seule fois par type*, dans ce cas une fois par `N` (sauf dans les cas particuliers où la fonction est générée plus d'une fois - voir la clause de non-responsabilité ci-dessus).

### Optionally-generated functions

Les fonctions générées peuvent atteindre une grande efficacité à l'exécution, mais cela entraîne un coût en temps de compilation : un nouveau corps de fonction doit être généré pour chaque combinaison de types d'arguments concrets. En général, Julia est capable de compiler des versions "génériques" de fonctions qui fonctionneront pour n'importe quels arguments, mais avec des fonctions générées, cela est impossible. Cela signifie que les programmes utilisant intensivement des fonctions générées pourraient être impossibles à compiler statiquement.

Pour résoudre ce problème, le langage fournit une syntaxe pour écrire des implémentations alternatives normales, non générées, de fonctions générées. Appliqué à l'exemple `sub2ind` ci-dessus, cela ressemblerait à ceci :

```jldoctest sub2ind_gen_opt
julia> function sub2ind_gen_impl(dims::Type{T}, I...) where T <: NTuple{N,Any} where N
           ex = :(I[$N] - 1)
           for i = (N - 1):-1:1
               ex = :(I[$i] - 1 + dims[$i] * $ex)
           end
           return :($ex + 1)
       end;

julia> function sub2ind_gen_fallback(dims::NTuple{N}, I) where N
           ind = I[N] - 1
           for i = (N - 1):-1:1
               ind = I[i] - 1 + dims[i]*ind
           end
           return ind + 1
       end;

julia> function sub2ind_gen(dims::NTuple{N}, I::Integer...) where N
           length(I) == N || error("partial indexing is unsupported")
           if @generated
               return sub2ind_gen_impl(dims, I...)
           else
               return sub2ind_gen_fallback(dims, I)
           end
       end;

julia> sub2ind_gen((3, 5), 1, 2)
4
```

En interne, ce code crée deux implémentations de la fonction : une générée où le premier bloc dans `if @generated` est utilisé, et une normale où le bloc `else` est utilisé. À l'intérieur de la partie `then` du bloc `if @generated`, le code a la même sémantique que d'autres fonctions générées : les noms des arguments se réfèrent à des types, et le code doit retourner une expression. Plusieurs blocs `if @generated` peuvent apparaître, auquel cas l'implémentation générée utilise tous les blocs `then` et l'implémentation alternative utilise tous les blocs `else`.

Remarquez que nous avons ajouté une vérification d'erreur au début de la fonction. Ce code sera commun aux deux versions et est du code d'exécution dans les deux versions (il sera cité et renvoyé comme une expression de la version générée). Cela signifie que les valeurs et les types des variables locales ne sont pas disponibles au moment de la génération du code – le code de génération de code ne peut voir que les types des arguments.

Dans ce style de définition, la fonctionnalité de génération de code est essentiellement une optimisation optionnelle. Le compilateur l'utilisera si cela est pratique, mais sinon, il peut choisir d'utiliser l'implémentation normale à la place. Ce style est préféré, car il permet au compilateur de prendre plus de décisions et de compiler les programmes de plusieurs manières, et parce que le code normal est plus lisible que le code générant du code. Cependant, l'implémentation utilisée dépend des détails d'implémentation du compilateur, il est donc essentiel que les deux implémentations se comportent de manière identique.
