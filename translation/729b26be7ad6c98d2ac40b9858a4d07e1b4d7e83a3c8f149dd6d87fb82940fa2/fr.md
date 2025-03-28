# [Scope of Variables](@id scope-of-variables)

Le *champ* d'une variable est la région de code dans laquelle une variable est accessible. La portée des variables aide à éviter les conflits de noms de variables. Le concept est intuitif : deux fonctions peuvent toutes deux avoir des arguments appelés `x` sans que les deux `x` ne se réfèrent à la même chose. De même, il existe de nombreux autres cas où différents blocs de code peuvent utiliser le même nom sans se référer à la même chose. Les règles concernant quand le même nom de variable se réfère ou ne se réfère pas à la même chose sont appelées règles de portée ; cette section les explique en détail.

Certaines constructions dans le langage introduisent des *blocs de portée*, qui sont des régions de code éligibles pour être la portée d'un ensemble de variables. La portée d'une variable ne peut pas être un ensemble arbitraire de lignes de code ; au lieu de cela, elle s'alignera toujours avec l'un de ces blocs. Il existe deux types principaux de portées en Julia, la *portée globale* et la *portée locale*. Cette dernière peut être imbriquée. Il y a également une distinction en Julia entre les constructions qui introduisent une "portée stricte" et celles qui n'introduisent qu'une "portée souple", ce qui affecte si [shadowing](https://en.wikipedia.org/wiki/Variable_shadowing) une variable globale du même nom est autorisée ou non.

### [Scope constructs](@id man-scope-table)

Les constructions introduisant des blocs de portée sont :

| Construct                                                                        | Scope type   | Allowed within |
|:-------------------------------------------------------------------------------- |:------------ |:-------------- |
| [`module`](@ref), [`baremodule`](@ref)                                           | global       | global         |
| [`struct`](@ref)                                                                 | local (soft) | global         |
| [`for`](@ref), [`while`](@ref), [`try`](@ref try)                                | local (soft) | global, local  |
| [`macro`](@ref)                                                                  | local (hard) | global         |
| functions, [`do`](@ref) blocks, [`let`](@ref) blocks, comprehensions, generators | local (hard) | global, local  |

Notamment absents de ce tableau sont [begin blocks](@ref man-compound-expressions) et [if blocks](@ref man-conditional-evaluation) qui ne *introduisent pas* de nouveaux scopes. Les trois types de scopes suivent des règles quelque peu différentes qui seront expliquées ci-dessous.

Julia utilise [lexical scoping](https://en.wikipedia.org/wiki/Scope_(computer_science)#Lexical_scope_vs._dynamic_scope), ce qui signifie que la portée d'une fonction n'hérite pas de la portée de son appelant, mais de la portée dans laquelle la fonction a été définie. Par exemple, dans le code suivant, le `x` à l'intérieur de `foo` fait référence au `x` dans la portée globale de son module `Bar` :

```jldoctest moduleBar
julia> module Bar
           x = 1
           foo() = x
       end;
```

et pas un `x` dans la portée où `foo` est utilisé :

```jldoctest moduleBar
julia> import .Bar

julia> x = -1;

julia> Bar.foo()
1
```

Ainsi, *la portée lexicale* signifie que ce à quoi une variable dans un morceau de code particulier fait référence peut être déduit du code dans lequel elle apparaît seule et ne dépend pas de la façon dont le programme s'exécute. Une portée imbriquée dans une autre portée peut "voir" les variables dans toutes les portées extérieures dans lesquelles elle est contenue. Les portées extérieures, en revanche, ne peuvent pas voir les variables dans les portées intérieures.

## Global Scope

Chaque module introduit un nouvel espace de noms global, distinct de l'espace de noms global de tous les autres modules—il n'y a pas d'espace de noms global englobant. Les modules peuvent introduire des variables d'autres modules dans leur espace de noms par le biais des déclarations [using or import](@ref modules) ou par un accès qualifié utilisant la notation par points, c'est-à-dire que chaque module est un soi-disant *espace de noms* ainsi qu'une structure de données de première classe associant des noms à des valeurs.

Si une expression de niveau supérieur contient une déclaration de variable avec le mot-clé `local`, alors cette variable n'est pas accessible en dehors de cette expression. La variable à l'intérieur de l'expression n'affecte pas les variables globales du même nom. Un exemple est de déclarer `local x` dans un bloc `begin` ou `if` au niveau supérieur :

```jldoctest
julia> x = 1
       begin
           local x = 0
           @show x
       end
       @show x;
x = 0
x = 1
```

Notez que l'invite interactive (également appelée REPL) est dans le scope global du module `Main`.

## [Local Scope](@id local-scope)

Un nouveau scope local est introduit par la plupart des blocs de code (voir ci-dessus [table](@ref man-scope-table) pour une liste complète). Si un tel bloc est syntactiquement imbriqué à l'intérieur d'un autre scope local, le scope qu'il crée est imbriqué à l'intérieur de tous les scopes locaux dans lesquels il apparaît, qui sont tous finalement imbriqués à l'intérieur du scope global du module dans lequel le code est évalué. Les variables dans les scopes extérieurs sont visibles depuis n'importe quel scope qu'elles contiennent — ce qui signifie qu'elles peuvent être lues et écrites dans les scopes intérieurs — à moins qu'il n'y ait une variable locale avec le même nom qui "cache" la variable extérieure du même nom. Cela est vrai même si le scope local extérieur est déclaré après (dans le sens textuel ci-dessous) un bloc intérieur. Lorsque nous disons qu'une variable "existe" dans un scope donné, cela signifie qu'une variable de ce nom existe dans n'importe lequel des scopes que le scope actuel contient, y compris le courant.

Certain langages de programmation nécessitent de déclarer explicitement de nouvelles variables avant de les utiliser. La déclaration explicite fonctionne également en Julia : dans n'importe quel scope local, écrire `local x` déclare une nouvelle variable locale dans ce scope, peu importe s'il existe déjà une variable nommée `x` dans un scope extérieur ou non. Cependant, déclarer chaque nouvelle variable de cette manière est quelque peu verbeux et fastidieux, donc Julia, comme beaucoup d'autres langages, considère qu'assigner à un nom de variable qui n'existe pas déjà déclare implicitement cette variable. Si le scope actuel est global, la nouvelle variable est globale ; si le scope actuel est local, la nouvelle variable est locale au scope local le plus interne et sera visible à l'intérieur de ce scope mais pas à l'extérieur. Si vous assignez à un local existant, cela *met toujours à jour* ce local existant : vous ne pouvez masquer un local qu'en déclarant explicitement un nouveau local dans un scope imbriqué avec le mot-clé `local`. En particulier, cela s'applique aux variables assignées dans des fonctions internes, ce qui peut surprendre les utilisateurs venant de Python où l'assignation dans une fonction interne crée un nouveau local à moins que la variable ne soit explicitement déclarée comme non locale.

Dans l'ensemble, c'est assez intuitif, mais comme pour beaucoup de choses qui se comportent de manière intuitive, les détails sont plus subtils qu'on ne pourrait naïvement l'imaginer.

Lorsque `x = <value>` se produit dans un scope local, Julia applique les règles suivantes pour décider ce que signifie l'expression en fonction de l'endroit où l'expression d'assignation se produit et de ce à quoi `x` fait déjà référence à cet endroit :

1. **Variable local existant :** Si `x` est *déjà une variable locale*, alors la variable locale existante `x` est assignée ;
2. **Portée stricte :** Si `x` *n'est pas déjà une variable locale* et qu'une affectation se produit à l'intérieur de tout construct de portée stricte (c'est-à-dire dans un bloc `let`, le corps d'une fonction ou d'une macro, une compréhension ou un générateur), une nouvelle variable locale nommée `x` est créée dans la portée de l'affectation ;
3. **Portée douce :** Si `x` *n'est pas déjà une variable locale* et que tous les constructeurs de portée contenant l'assignation sont des portées douces (boucles, blocs `try`/`catch`, ou blocs `struct`), le comportement dépend de la définition de la variable globale `x` :

      * si `x` global est *indéfini*, un nouveau local nommé `x` est créé dans le scope de l'assignation ;
      * si la variable globale `x` est *définie*, l'assignation est considérée comme ambiguë :

          * dans des contextes *non interactifs* (fichiers, évaluation), un avertissement d'ambiguïté est imprimé et un nouveau local est créé ;
          * dans des contextes *interactifs* (REPL, notebooks), la variable globale `x` est assignée.

Vous pouvez noter que dans des contextes non interactifs, les comportements de portée dure et souple sont identiques, sauf qu'un avertissement est imprimé lorsqu'une variable implicitement locale (c'est-à-dire non déclarée avec `local x`) masque une variable globale. Dans des contextes interactifs, les règles suivent une heuristique plus complexe pour des raisons de commodité. Cela est couvert en profondeur dans les exemples qui suivent.

Maintenant que vous connaissez les règles, examinons quelques exemples. Chaque exemple est supposé être évalué dans une nouvelle session REPL afin que les seules variables globales dans chaque extrait soient celles qui sont assignées dans ce bloc de code.

Nous commencerons par une situation claire et nette : une affectation à l'intérieur d'un champ de portée stricte, dans ce cas le corps d'une fonction, lorsque aucune variable locale portant ce nom n'existe déjà :

```jldoctest
julia> function greet()
           x = "hello" # new local
           println(x)
       end
greet (generic function with 1 method)

julia> greet()
hello

julia> x # global
ERROR: UndefVarError: `x` not defined in `Main`
```

À l'intérieur de la fonction `greet`, l'assignation `x = "hello"` fait que `x` devient une nouvelle variable locale dans le scope de la fonction. Il y a deux faits pertinents : l'assignation se produit dans le scope local et il n'existe pas de variable locale `x` existante. Puisque `x` est local, peu importe s'il y a un `x` global nommé ou non. Ici, par exemple, nous définissons `x = 123` avant de définir et d'appeler `greet` :

```jldoctest
julia> x = 123 # global
123

julia> function greet()
           x = "hello" # new local
           println(x)
       end
greet (generic function with 1 method)

julia> greet()
hello

julia> x # global
123
```

Puisque le `x` dans `greet` est local, la valeur (ou son absence) du global `x` n'est pas affectée par l'appel de `greet`. La règle de portée stricte ne se soucie pas de savoir si un global nommé `x` existe ou non : l'assignation à `x` dans une portée stricte est locale (à moins que `x` ne soit déclaré global).

La prochaine situation claire que nous allons considérer est celle où il existe déjà une variable locale nommée `x`, auquel cas `x = <value>` assigne toujours à ce `x` local existant. Cela est vrai que l'assignation se produise dans la même portée locale, dans une portée locale interne dans le même corps de fonction, ou dans le corps d'une fonction imbriquée à l'intérieur d'une autre fonction, également connue sous le nom de [closure](https://en.wikipedia.org/wiki/Closure_(computer_programming)).

Nous allons utiliser la fonction `sum_to`, qui calcule la somme des entiers de un jusqu'à `n`, comme exemple :

```julia
function sum_to(n)
    s = 0 # new local
    for i = 1:n
        s = s + i # assign existing local
    end
    return s # same local
end
```

Comme dans l'exemple précédent, la première affectation à `s` en haut de `sum_to` fait de `s` une nouvelle variable locale dans le corps de la fonction. La boucle `for` a son propre champ lexical local à l'intérieur du champ lexical de la fonction. Au moment où `s = s + i` se produit, `s` est déjà une variable locale, donc l'affectation met à jour le `s` existant au lieu de créer un nouveau local. Nous pouvons tester cela en appelant `sum_to` dans le REPL :

```jldoctest
julia> function sum_to(n)
           s = 0 # new local
           for i = 1:n
               s = s + i # assign existing local
           end
           return s # same local
       end
sum_to (generic function with 1 method)

julia> sum_to(10)
55

julia> s # global
ERROR: UndefVarError: `s` not defined in `Main`
```

Puisque `s` est local à la fonction `sum_to`, appeler la fonction n'a aucun effet sur la variable globale `s`. Nous pouvons également voir que la mise à jour `s = s + i` dans la boucle `for` doit avoir mis à jour le même `s` créé par l'initialisation `s = 0` puisque nous obtenons la somme correcte de 55 pour les entiers de 1 à 10.

Examinons le fait que le corps de la boucle `for` a son propre scope pendant une seconde en écrivant une variation légèrement plus verbeuse que nous appellerons `sum_to_def`, dans laquelle nous sauvegardons la somme `s + i` dans une variable `t` avant de mettre à jour `s` :

```jldoctest
julia> function sum_to_def(n)
           s = 0 # new local
           for i = 1:n
               t = s + i # new local `t`
               s = t # assign existing local `s`
           end
           return s, @isdefined(t)
       end
sum_to_def (generic function with 1 method)

julia> sum_to_def(10)
(55, false)
```

Cette version renvoie `s` comme auparavant, mais elle utilise également le macro `@isdefined` pour renvoyer un booléen indiquant s'il existe une variable locale nommée `t` définie dans la portée locale la plus externe de la fonction. Comme vous pouvez le voir, il n'y a pas de `t` défini en dehors du corps de la boucle `for`. Cela est dû à la règle de portée stricte : puisque l'assignation à `t` se produit à l'intérieur d'une fonction, qui introduit une portée stricte, l'assignation fait que `t` devient une nouvelle variable locale dans la portée locale où elle apparaît, c'est-à-dire à l'intérieur du corps de la boucle. Même s'il y avait un global nommé `t`, cela ne ferait aucune différence : la règle de portée stricte n'est pas affectée par quoi que ce soit dans la portée globale.

Notez que la portée locale d'un corps de boucle for n'est pas différente de la portée locale d'une fonction interne. Cela signifie que nous pourrions réécrire cet exemple de sorte que le corps de la boucle soit implémenté comme un appel à une fonction d'assistance interne et qu'il se comporte de la même manière :

```jldoctest
julia> function sum_to_def_closure(n)
           function loop_body(i)
               t = s + i # new local `t`
               s = t # assign same local `s` as below
           end
           s = 0 # new local
           for i = 1:n
               loop_body(i)
           end
           return s, @isdefined(t)
       end
sum_to_def_closure (generic function with 1 method)

julia> sum_to_def_closure(10)
(55, false)
```

Cet exemple illustre quelques points clés :

1. Les portées des fonctions internes sont comme n'importe quelle autre portée locale imbriquée. En particulier, si une variable est déjà locale à l'extérieur d'une fonction interne et que vous lui assignez une valeur dans la fonction interne, la variable locale extérieure est mise à jour.
2. Peu importe si la définition d'un local externe se produit en dessous de son actualisation, la règle reste la même. L'ensemble de la portée locale englobante est analysé et ses locaux déterminés avant que les significations des locaux internes ne soient résolues.

Ce design signifie que vous pouvez généralement déplacer du code dans ou hors d'une fonction interne sans changer son sens, ce qui facilite un certain nombre d'idiomes courants dans le langage utilisant des fermetures (voir [do blocks](@ref Do-Block-Syntax-for-Function-Arguments)).

Passons à des cas plus ambigus couverts par la règle de portée douce. Nous allons explorer cela en extrayant les corps des fonctions `greet` et `sum_to_def` dans des contextes de portée douce. Tout d'abord, plaçons le corps de `greet` dans une boucle `for`—qui est douce, plutôt que dure—et évaluons-le dans le REPL :

```jldoctest
julia> for i = 1:3
           x = "hello" # new local
           println(x)
       end
hello
hello
hello

julia> x
ERROR: UndefVarError: `x` not defined in `Main`
```

Puisque le `x` global n'est pas défini lorsque la boucle `for` est évaluée, la première clause de la règle de portée douce s'applique et `x` est créé comme local à la boucle `for`, et donc le `x` global reste indéfini après l'exécution de la boucle. Ensuite, considérons le corps de `sum_to_def` extrait dans la portée globale, en fixant son argument à `n = 10`.

```julia
s = 0
for i = 1:10
    t = s + i
    s = t
end
s
@isdefined(t)
```

Que fait ce code ? Indice : c'est une question piège. La réponse est "cela dépend." Si ce code est saisi de manière interactive, il se comporte de la même manière que dans le corps d'une fonction. Mais si le code apparaît dans un fichier, il affiche un avertissement d'ambiguïté et lance une erreur de variable indéfinie. Voyons-le fonctionner dans le REPL d'abord :

```jldoctest
julia> s = 0 # global
0

julia> for i = 1:10
           t = s + i # new local `t`
           s = t # assign global `s`
       end

julia> s # global
55

julia> @isdefined(t) # global
false
```

Le REPL approche le fait d'être dans le corps d'une fonction en décidant si l'assignation à l'intérieur de la boucle assigne à une variable globale ou crée une nouvelle variable locale en fonction de l'existence d'une variable globale portant ce nom. Si une variable globale du même nom existe, alors l'assignation la met à jour. Si aucune variable globale n'existe, alors l'assignation crée une nouvelle variable locale. Dans cet exemple, nous voyons les deux cas en action :

  * Il n'y a pas de global nommé `t`, donc `t = s + i` crée un nouveau `t` qui est local à la boucle `for`;
  * Il y a une variable globale nommée `s`, donc `s = t` lui assigne une valeur.

Le deuxième fait est la raison pour laquelle l'exécution de la boucle modifie la valeur globale de `s` et le premier fait est la raison pour laquelle `t` est toujours indéfini après l'exécution de la boucle. Maintenant, essayons d'évaluer ce même code comme s'il était dans un fichier à la place :

```jldoctest
julia> code = """
       s = 0 # global
       for i = 1:10
           t = s + i # new local `t`
           s = t # new local `s` with warning
       end
       s, # global
       @isdefined(t) # global
       """;

julia> include_string(Main, code)
┌ Warning: Assignment to `s` in soft scope is ambiguous because a global variable by the same name exists: `s` will be treated as a new local. Disambiguate by using `local s` to suppress this warning or `global s` to assign to the existing global variable.
└ @ string:4
ERROR: LoadError: UndefVarError: `s` not defined in local scope
```

Ici, nous utilisons [`include_string`](@ref), pour évaluer `code` comme s'il s'agissait du contenu d'un fichier. Nous pourrions également enregistrer `code` dans un fichier, puis appeler `include` sur ce fichier—le résultat serait le même. Comme vous pouvez le voir, cela se comporte de manière très différente de l'évaluation du même code dans le REPL. Décomposons ce qui se passe ici :

  * global `s` est défini avec la valeur `0` avant que la boucle ne soit évaluée.
  * l'assignation `s = t` se produit dans une portée douce—une boucle `for` en dehors de tout corps de fonction ou autre construction de portée stricte
  * par conséquent, la deuxième clause de la règle de portée douce s'applique, et l'affectation est ambiguë, donc un avertissement est émis
  * l'exécution continue, rendant `s` local au corps de la boucle `for`
  * puisque `s` est local à la boucle `for`, il est indéfini lorsque `t = s + i` est évalué, ce qui provoque une erreur
  * l'évaluation s'arrête là, mais si elle atteignait `s` et `@isdefined(t)`, elle retournerait `0` et `false`.

Cela démontre certains aspects importants de la portée : dans une portée, chaque variable ne peut avoir qu'une seule signification, et cette signification est déterminée indépendamment de l'ordre des expressions. La présence de l'expression `s = t` dans la boucle fait que `s` est local à la boucle, ce qui signifie qu'il est également local lorsqu'il apparaît du côté droit de `t = s + i`, même si cette expression apparaît en premier et est évaluée en premier. On pourrait imaginer que le `s` sur la première ligne de la boucle pourrait être global tandis que le `s` sur la deuxième ligne de la boucle est local, mais ce n'est pas possible puisque les deux lignes se trouvent dans le même bloc de portée et chaque variable ne peut signifier qu'une seule chose dans une portée donnée.

#### [On Soft Scope](@id on-soft-scope)

Nous avons maintenant couvert toutes les règles de portée locale, mais avant de conclure cette section, peut-être quelques mots devraient être dits sur pourquoi le cas de portée douce ambigu est traité différemment dans les contextes interactifs et non interactifs. Il y a deux questions évidentes que l'on pourrait poser :

1. Pourquoi cela ne fonctionne-t-il pas simplement comme le REPL partout ?
2. Pourquoi cela ne fonctionne-t-il pas comme dans les fichiers partout ? Et peut-être ignorer l'avertissement ?

En Julia ≤ 0.6, tous les portées globales fonctionnaient comme le REPL actuel : lorsque `x = <valeur>` se produisait dans une boucle (ou `try`/`catch`, ou corps de `struct`) mais en dehors d'un corps de fonction (ou bloc `let` ou compréhension), il était décidé en fonction de la présence ou non d'un `x` global nommé si `x` devait être local à la boucle. Ce comportement a l'avantage d'être intuitif et pratique puisqu'il s'approche le plus possible du comportement à l'intérieur d'un corps de fonction. En particulier, il facilite le déplacement de code entre un corps de fonction et le REPL lors de la tentative de débogage du comportement d'une fonction. Cependant, cela a quelques inconvénients. Tout d'abord, c'est un comportement assez complexe : de nombreuses personnes au fil des ans ont été confuses à propos de ce comportement et se sont plaintes qu'il était compliqué et difficile à expliquer et à comprendre. Point juste. Deuxièmement, et peut-être pire, c'est que c'est mauvais pour la programmation "à grande échelle". Lorsque vous voyez un petit morceau de code à un endroit comme celui-ci, il est assez clair ce qui se passe :

```julia
s = 0
for i = 1:10
    s += i
end
```

Évidemment, l'intention est de modifier la variable globale existante `s`. Que pourrait-il signifier d'autre ? Cependant, tout le code du monde réel n'est pas aussi court ou aussi clair. Nous avons constaté que du code comme le suivant se rencontre souvent dans la nature :

```julia
x = 123

# much later
# maybe in a different file

for i = 1:10
    x = "hello"
    println(x)
end

# much later
# maybe in yet another file
# or maybe back in the first one where `x = 123`

y = x + 234
```

Il est beaucoup moins clair ce qui devrait se passer ici. Puisque `x + "hello"` est une erreur de méthode, il semble probable que l'intention soit que `x` soit local à la boucle `for`. Mais les valeurs d'exécution et les méthodes qui existent ne peuvent pas être utilisées pour déterminer les portées des variables. Avec le comportement de Julia ≤ 0.6, il est particulièrement préoccupant que quelqu'un ait pu écrire la boucle `for` en premier, qu'elle fonctionnait très bien, mais qu'ensuite, lorsque quelqu'un d'autre ajoute un nouveau global éloigné—possiblement dans un fichier différent—le code change soudainement de signification et soit casse bruyamment ou, pire encore, fait silencieusement la mauvaise chose. Ce genre de ["spooky action at a distance"](https://en.wikipedia.org/wiki/Action_at_a_distance_(computer_programming)) est quelque chose que de bonnes conceptions de langages de programmation devraient prévenir.

Donc, dans Julia 1.0, nous avons simplifié les règles de portée : dans n'importe quelle portée locale, l'assignation à un nom qui n'était pas déjà une variable locale créait une nouvelle variable locale. Cela a éliminé la notion de portée douce dans son ensemble et a également supprimé le potentiel d'action spooky. Nous avons découvert et corrigé un nombre significatif de bogues en raison de la suppression de la portée douce, justifiant le choix de s'en débarrasser. Et il y a eu beaucoup de réjouissances ! Eh bien, non, pas vraiment. Parce que certaines personnes étaient en colère de devoir maintenant écrire :

```julia
s = 0
for i = 1:10
    global s += i
end
```

Voyez-vous cette annotation `global` là-dedans ? Horrible. Évidemment, cette situation ne pouvait pas être tolérée. Mais sérieusement, il y a deux problèmes principaux avec le fait de nécessiter `global` pour ce type de code au niveau supérieur :

1. Il n'est plus pratique de copier et coller le code à l'intérieur d'un corps de fonction dans le REPL pour le déboguer—vous devez ajouter des annotations `global` puis les supprimer à nouveau pour revenir en arrière ;
2. Les débutants écriront ce genre de code sans le `global` et n'auront aucune idée de pourquoi leur code ne fonctionne pas—l'erreur qu'ils obtiennent est que `s` est indéfini, ce qui ne semble éclairer personne qui fait cette erreur.

À partir de Julia 1.5, ce code fonctionne sans l'annotation `global` dans des contextes interactifs comme le REPL ou les notebooks Jupyter (tout comme Julia 0.6) et dans des fichiers et d'autres contextes non interactifs, il affiche cet avertissement très direct :

> L'assignation à `s` dans le scope souple est ambiguë car une variable globale du même nom existe : `s` sera traité comme un nouveau local. Désambiguisez en utilisant `local s` pour supprimer cet avertissement ou `global s` pour assigner à la variable globale existante.


Cela aborde les deux problèmes tout en préservant les avantages du "programmation à grande échelle" du comportement 1.0 : les variables globales n'ont aucun effet étrange sur le sens du code qui peut être éloigné ; dans le REPL, le débogage par copier-coller fonctionne et les débutants n'ont aucun problème ; chaque fois que quelqu'un oublie une annotation `global` ou ombre accidentellement une variable globale existante avec une locale dans une portée douce, ce qui serait de toute façon déroutant, il reçoit un avertissement clair.

Une propriété importante de ce design est que tout code qui s'exécute dans un fichier sans avertissement se comportera de la même manière dans un nouveau REPL. Et inversement, si vous prenez une session REPL et que vous l'enregistrez dans un fichier, si elle se comporte différemment de ce qu'elle faisait dans le REPL, alors vous recevrez un avertissement.

### Let Blocks

`let` les déclarations créent un nouveau bloc de *portée stricte* (voir ci-dessus) et introduisent de nouvelles liaisons de variables chaque fois qu'elles s'exécutent. La variable n'a pas besoin d'être immédiatement assignée :

```jldoctest
julia> var1 = let x
           for i in 1:5
               (i == 4) && (x = i; break)
           end
           x
       end
4
```

Alors que les affectations peuvent réaffecter une nouvelle valeur à un emplacement de valeur existant, `let` crée toujours un nouvel emplacement. Cette différence n'est généralement pas importante et n'est détectable que dans le cas de variables qui survivent à leur portée via des fermetures. La syntaxe `let` accepte une série d'affectations et de noms de variables séparés par des virgules :

```jldoctest
julia> x, y, z = -1, -1, -1;

julia> let x = 1, z
           println("x: $x, y: $y") # x is local variable, y the global
           println("z: $z") # errors as z has not been assigned yet but is local
       end
x: 1, y: -1
ERROR: UndefVarError: `z` not defined in local scope
```

Les affectations sont évaluées dans l'ordre, chaque côté droit étant évalué dans le contexte avant que la nouvelle variable du côté gauche ne soit introduite. Il est donc logique d'écrire quelque chose comme `let x = x` puisque les deux variables `x` sont distinctes et ont un stockage séparé. Voici un exemple où le comportement de `let` est nécessaire :

```jldoctest
julia> Fs = Vector{Any}(undef, 2); i = 1;

julia> while i <= 2
           Fs[i] = ()->i
           global i += 1
       end

julia> Fs[1]()
3

julia> Fs[2]()
3
```

Ici, nous créons et stockons deux fermetures qui retournent la variable `i`. Cependant, c'est toujours la même variable `i`, donc les deux fermetures se comportent de manière identique. Nous pouvons utiliser `let` pour créer une nouvelle liaison pour `i` :

```jldoctest
julia> Fs = Vector{Any}(undef, 2); i = 1;

julia> while i <= 2
           let i = i
               Fs[i] = ()->i
           end
           global i += 1
       end

julia> Fs[1]()
1

julia> Fs[2]()
2
```

Puisque la construction `begin` n'introduit pas un nouveau scope, il peut être utile d'utiliser un `let` sans argument pour simplement introduire un nouveau bloc de scope sans créer immédiatement de nouvelles liaisons :

```jldoctest
julia> let
           local x = 1
           let
               local x = 2
           end
           x
       end
1
```

Puisque `let` introduit un nouveau bloc de portée, le `x` local interne est une variable différente de l'`x` local externe. Cet exemple particulier est équivalent à :

```jldoctest
julia> let x = 1
           let x = 2
           end
           x
       end
1
```

### Loops and Comprehensions

In loops and [comprehensions](@ref man-comprehensions), new variables introduced in their body scopes are freshly allocated for each loop iteration, as if the loop body were surrounded by a `let` block, as demonstrated by this example:

```jldoctest
julia> Fs = Vector{Any}(undef, 2);

julia> for j = 1:2
           Fs[j] = ()->j
       end

julia> Fs[1]()
1

julia> Fs[2]()
2
```

Une variable d'itération de boucle `for` ou de compréhension est toujours une nouvelle variable :

```julia-repl enable_doctest_when_deprecation_warning_is_removed
julia> function f()
           i = 0
           for i = 1:3
               # empty
           end
           return i
       end;

julia> f()
0
```

Cependant, il est parfois utile de réutiliser une variable locale existante comme variable d'itération. Cela peut être fait facilement en ajoutant le mot-clé `outer` :

```jldoctest
julia> function f()
           i = 0
           for outer i = 1:3
               # empty
           end
           return i
       end;

julia> f()
3
```

## Constants

Une utilisation courante des variables consiste à donner des noms à des valeurs spécifiques et immuables. Ces variables ne sont assignées qu'une seule fois. Cette intention peut être transmise au compilateur en utilisant le mot-clé [`const`](@ref) :

```jldoctest
julia> const e  = 2.71828182845904523536;

julia> const pi = 3.14159265358979323846;
```

Plusieurs variables peuvent être déclarées dans une seule instruction `const` :

```jldoctest
julia> const a, b = 1, 2
(1, 2)
```

La déclaration `const` ne doit être utilisée qu'au niveau global pour les variables globales. Il est difficile pour le compilateur d'optimiser le code impliquant des variables globales, car leurs valeurs (ou même leurs types) peuvent changer à presque tout moment. Si une variable globale ne changera pas, ajouter une déclaration `const` résout ce problème de performance.

Les constantes locales sont assez différentes. Le compilateur est capable de déterminer automatiquement quand une variable locale est constante, donc les déclarations de constantes locales ne sont pas nécessaires et, en fait, ne sont actuellement pas prises en charge.

Les affectations spéciales de niveau supérieur, telles que celles effectuées par les mots-clés `function` et `struct`, sont constantes par défaut.

Notez que `const` n'affecte que la liaison de la variable ; la variable peut être liée à un objet mutable (comme un tableau), et cet objet peut toujours être modifié. De plus, lorsque l'on essaie d'assigner une valeur à une variable déclarée constante, les scénarios suivants sont possibles :

  * si une nouvelle valeur a un type différent de celui de la constante, alors une erreur est levée :

```jldoctest
julia> const x = 1.0
1.0

julia> x = 1
ERROR: invalid redefinition of constant x
```

  * si une nouvelle valeur a le même type que la constante, alors un avertissement est imprimé :

```jldoctest
julia> const y = 1.0
1.0

julia> y = 2.0
WARNING: redefinition of constant y. This may fail, cause incorrect answers, or produce other errors.
2.0
```

  * si une affectation ne devait pas entraîner de changement de la valeur de la variable, aucun message n'est donné :

```jldoctest
julia> const z = 100
100

julia> z = 100
100
```

La dernière règle s'applique aux objets immuables même si la liaison de la variable change, par exemple :

```julia-repl
julia> const s1 = "1"
"1"

julia> s2 = "1"
"1"

julia> pointer.([s1, s2], 1)
2-element Array{Ptr{UInt8},1}:
 Ptr{UInt8} @0x00000000132c9638
 Ptr{UInt8} @0x0000000013dd3d18

julia> s1 = s2
"1"

julia> pointer.([s1, s2], 1)
2-element Array{Ptr{UInt8},1}:
 Ptr{UInt8} @0x0000000013dd3d18
 Ptr{UInt8} @0x0000000013dd3d18
```

Cependant, pour les objets mutables, l'avertissement est imprimé comme prévu :

```jldoctest
julia> const a = [1]
1-element Vector{Int64}:
 1

julia> a = [1]
WARNING: redefinition of constant a. This may fail, cause incorrect answers, or produce other errors.
1-element Vector{Int64}:
 1
```

Notez que bien que cela soit parfois possible, changer la valeur d'une variable `const` est fortement déconseillé et est destiné uniquement à des fins de commodité lors d'une utilisation interactive. Changer des constantes peut causer divers problèmes ou comportements inattendus. Par exemple, si une méthode fait référence à une constante et est déjà compilée avant que la constante ne soit changée, elle pourrait continuer à utiliser l'ancienne valeur :

```jldoctest
julia> const x = 1
1

julia> f() = x
f (generic function with 1 method)

julia> f()
1

julia> x = 2
WARNING: redefinition of constant x. This may fail, cause incorrect answers, or produce other errors.
2

julia> f()
1
```

## [Typed Globals](@id man-typed-globals)

!!! compat "Julia 1.8"
    Le support pour les globals typés a été ajouté dans Julia 1.8


Similaire à la déclaration en tant que constantes, les liaisons globales peuvent également être déclarées pour être toujours d'un type constant. Cela peut être fait soit sans assigner une valeur réelle en utilisant la syntaxe `global x::T`, soit lors de l'assignation comme `x::T = 123`.

```jldoctest
julia> x::Float64 = 2.718
2.718

julia> f() = x
f (generic function with 1 method)

julia> Base.return_types(f)
1-element Vector{Any}:
 Float64
```

Pour toute affectation à un global, Julia essaiera d'abord de le convertir au type approprié en utilisant [`convert`](@ref) :

```jldoctest
julia> global y::Int

julia> y = 1.0
1.0

julia> y
1

julia> y = 3.14
ERROR: InexactError: Int64(3.14)
Stacktrace:
[...]
```

Le type n'a pas besoin d'être concret, mais les annotations avec des types abstraits ont généralement peu de bénéfices en termes de performance.

Une fois qu'un global a été assigné ou que son type a été défini, le type de liaison n'est pas autorisé à changer :

```jldoctest
julia> x = 1
1

julia> global x::Int
ERROR: cannot set type for global x. It already has a value or is already set to a different type.
Stacktrace:
[...]
```
