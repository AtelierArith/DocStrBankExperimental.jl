# Julia Functions

Ce document expliquera comment fonctionnent les fonctions, les définitions de méthodes et les tables de méthodes.

## Method Tables

Chaque fonction en Julia est une fonction générique. Une fonction générique est conceptuellement une seule fonction, mais se compose de nombreuses définitions, ou méthodes. Les méthodes d'une fonction générique sont stockées dans une table de méthodes. Les tables de méthodes (type `MethodTable`) sont associées à des `TypeName`. Un `TypeName` décrit une famille de types paramétrés. Par exemple, `Complex{Float32}` et `Complex{Float64}` partagent le même objet de nom de type `Complex`.

Tous les objets en Julia sont potentiellement appelables, car chaque objet a un type, qui à son tour a un `TypeName`.

## [Function calls](@id Function-calls)

Étant donné l'appel `f(x, y)`, les étapes suivantes sont effectuées : d'abord, la méthode de table à utiliser est accédée sous la forme `typeof(f).name.mt`. Deuxièmement, un type de tuple d'arguments est formé, `Tuple{typeof(f), typeof(x), typeof(y)}`. Notez que le type de la fonction elle-même est le premier élément. Cela est dû au fait que le type peut avoir des paramètres, et doit donc participer à la dispatch. Ce type de tuple est recherché dans la table des méthodes.

Ce processus de dispatch est effectué par `jl_apply_generic`, qui prend deux arguments : un pointeur vers un tableau des valeurs `f`, `x` et `y`, et le nombre de valeurs (dans ce cas 3).

Dans tout le système, il existe deux types d'API qui gèrent les fonctions et les listes d'arguments : celles qui acceptent la fonction et les arguments séparément, et celles qui acceptent une seule structure d'argument. Dans le premier type d'API, la partie "arguments" ne contient *pas* d'informations sur la fonction, car celle-ci est transmise séparément. Dans le deuxième type d'API, la fonction est le premier élément de la structure d'argument.

Par exemple, la fonction suivante pour effectuer un appel accepte uniquement un pointeur `args`, donc le premier élément du tableau args sera la fonction à appeler :

```c
jl_value_t *jl_apply(jl_value_t **args, uint32_t nargs)
```

Ce point d'entrée pour la même fonctionnalité accepte la fonction séparément, donc le tableau `args` ne contient pas la fonction :

```c
jl_value_t *jl_call(jl_function_t *f, jl_value_t **args, int32_t nargs);
```

## Adding methods

Étant donné le processus d'envoi ci-dessus, conceptuellement, tout ce qui est nécessaire pour ajouter une nouvelle méthode est (1) un type de tuple, et (2) du code pour le corps de la méthode. `jl_method_def` implémente cette opération. `jl_method_table_for` est appelé pour extraire la table de méthodes pertinente à partir de ce qui serait le type du premier argument. Cela est beaucoup plus compliqué que la procédure correspondante lors de l'envoi, car le type de tuple d'argument pourrait être abstrait. Par exemple, nous pouvons définir :

```julia
(::Union{Foo{Int},Foo{Int8}})(x) = 0
```

ce qui fonctionne puisque toutes les méthodes de correspondance possibles appartiendraient à la même table de méthodes.

## Creating generic functions

Puisque chaque objet est appelable, rien de spécial n'est nécessaire pour créer une fonction générique. Par conséquent, `jl_new_generic_function` crée simplement un nouveau sous-type singleton (de taille 0) de `Function` et renvoie son instance. Une fonction peut avoir un "nom d'affichage" mnémotechnique qui est utilisé dans les informations de débogage et lors de l'impression des objets. Par exemple, le nom de `Base.sin` est `sin`. Par convention, le nom du *type* créé est le même que le nom de la fonction, avec un `#` ajouté au début. Ainsi, `typeof(sin)` est `Base.#sin`.

## Closures

Une fermeture est simplement un objet appelable avec des noms de champ correspondant aux variables capturées. Par exemple, le code suivant :

```julia
function adder(x)
    return y->x+y
end
```

est abaissé à (environ) :

```julia
struct ##1{T}
    x::T
end

(_::##1)(y) = _.x + y

function adder(x)
    return ##1(x)
end
```

## Constructors

Un appel de constructeur est simplement un appel à un type. La table des méthodes pour `Type` contient toutes les définitions de constructeur. Tous les sous-types de `Type` (`Type`, `UnionAll`, `Union` et `DataType`) partagent actuellement une table des méthodes via un arrangement spécial.

## Builtins

Les fonctions "builtin", définies dans le module `Core`, sont :

```@eval
function lines(words)
    io = IOBuffer()
    n = 0
    for w in words
        if n+length(w) > 80
            print(io, '\n', w)
            n = length(w)
        elseif n == 0
            print(io, w);
            n += length(w)
        else
            print(io, ' ', w);
            n += length(w)+1
        end
    end
    String(take!(io))
end
import Markdown
[string(n) for n in names(Core;all=true)
    if getfield(Core,n) isa Core.Builtin && nameof(getfield(Core,n)) === n] |>
    lines |>
    s ->  "```\n$s\n```" |>
    Markdown.parse
```

Ce sont tous des objets singleton dont les types sont des sous-types de `Builtin`, qui est un sous-type de `Function`. Leur but est d'exposer des points d'entrée dans le temps d'exécution qui utilisent la convention d'appel "jlcall" :

```c
jl_value_t *(jl_value_t*, jl_value_t**, uint32_t)
```

Les tables de méthodes des builtins sont vides. Au lieu de cela, elles ont une seule entrée de cache de méthode attrape-tout (`Tuple{Vararg{Any}}`) dont le pointeur fptr jlcall pointe vers la fonction correcte. C'est une sorte de hack mais cela fonctionne raisonnablement bien.

## Keyword arguments

Les arguments de mots-clés fonctionnent en ajoutant des méthodes à la fonction kwcall. Cette fonction est généralement le "trieur d'arguments de mots-clés" ou "trieur de mots-clés", qui appelle ensuite le corps interne de la fonction (définie de manière anonyme). Chaque définition dans la fonction kwsorter a les mêmes arguments qu'une définition dans la table de méthodes normale, sauf qu'un seul argument `NamedTuple` est préfixé, ce qui donne les noms et les valeurs des arguments de mots-clés passés. Le travail du kwsorter est de déplacer les arguments de mots-clés dans leurs positions canoniques en fonction du nom, plus d'évaluer et de substituer toute expression de valeur par défaut nécessaire. Le résultat est une liste d'arguments positionnels normale, qui est ensuite passée à une autre fonction générée par le compilateur.

La manière la plus simple de comprendre le processus est de regarder comment une définition de méthode avec des arguments de mot-clé est simplifiée. Le code :

```julia
function circle(center, radius; color = black, fill::Bool = true, options...)
    # draw
end
```

produit en fait *trois* définitions de méthode. La première est une fonction qui accepte tous les arguments (y compris les arguments nommés) en tant qu'arguments positionnels, et inclut le code pour le corps de la méthode. Elle a un nom généré automatiquement :

```julia
function #circle#1(color, fill::Bool, options, circle, center, radius)
    # draw
end
```

La deuxième méthode est une définition ordinaire de la fonction `circle` originale, qui gère le cas où aucun argument clé n'est passé :

```julia
function circle(center, radius)
    #circle#1(black, true, pairs(NamedTuple()), circle, center, radius)
end
```

Cela envoie simplement à la première méthode, en passant les valeurs par défaut. `pairs` est appliqué au tuple nommé des arguments restants pour fournir une itération clé-valeur. Notez que si la méthode n'accepte pas les arguments de mot-clé restants, alors cet argument est absent.

Enfin, voici la définition de kwsorter :

```
function (::Core.kwftype(typeof(circle)))(kws, circle, center, radius)
    if haskey(kws, :color)
        color = kws.color
    else
        color = black
    end
    # etc.

    # put remaining kwargs in `options`
    options = structdiff(kws, NamedTuple{(:color, :fill)})

    # if the method doesn't accept rest keywords, throw an error
    # unless `options` is empty

    #circle#1(color, fill, pairs(options), circle, center, radius)
end
```

La fonction `Core.kwftype(t)` crée le champ `t.name.mt.kwsorter` (s'il n'a pas encore été créé) et retourne le type de cette fonction.

Ce design a la caractéristique que les sites d'appel qui n'utilisent pas d'arguments nommés ne nécessitent aucun traitement spécial ; tout fonctionne comme s'ils ne faisaient pas partie du langage du tout. Les sites d'appel qui utilisent des arguments nommés sont directement dispatchés au kwsorter de la fonction appelée. Par exemple, l'appel :

```julia
circle((0, 0), 1.0, color = red; other...)
```

est abaissé à :

```julia
kwcall(merge((color = red,), other), circle, (0, 0), 1.0)
```

`kwcall` (également dans `Core`) désigne une signature et un dispatch de kwcall. L'opération de splatting de mots-clés (écrite comme `other...`) appelle la fonction `merge` du tuple nommé. Cette fonction décompresse davantage chaque *élément* de `other`, s'attendant à ce que chacun contienne deux valeurs (un symbole et une valeur). Naturellement, une implémentation plus efficace est disponible si tous les arguments splattés sont des tuples nommés. Remarquez que la fonction `circle` d'origine est transmise pour gérer les fermetures.

## [Compiler efficiency issues](@id compiler-efficiency-issues)

Générer un nouveau type pour chaque fonction a des conséquences potentiellement graves sur l'utilisation des ressources du compilateur lorsqu'il est combiné avec le design de Julia qui "se spécialise par défaut sur tous les arguments". En effet, l'implémentation initiale de ce design a souffert de temps de construction et de test beaucoup plus longs, d'une utilisation de mémoire plus élevée et d'une image système presque 2 fois plus grande que la référence. Dans une implémentation naïve, le problème est suffisamment grave pour rendre le système presque inutilisable. Plusieurs optimisations significatives étaient nécessaires pour rendre le design pratique.

Le premier problème est la spécialisation excessive des fonctions pour différentes valeurs d'arguments de type fonction. De nombreuses fonctions se contentent simplement de "transmettre" un argument ailleurs, par exemple à une autre fonction ou à un emplacement de stockage. De telles fonctions n'ont pas besoin d'être spécialisées pour chaque fermeture qui pourrait être passée. Heureusement, ce cas est facile à distinguer en considérant simplement si une fonction *appelle* l'un de ses arguments (c'est-à-dire que l'argument apparaît en "position tête" quelque part). Les fonctions d'ordre supérieur critiques pour la performance comme `map` appellent certainement leur fonction d'argument et seront donc toujours spécialisées comme prévu. Cette optimisation est mise en œuvre en enregistrant quels arguments sont appelés lors du passage `analyze-variables` dans le front-end. Lorsque `cache_method` voit un argument dans la hiérarchie de type `Function` passé à un emplacement déclaré comme `Any` ou `Function`, il se comporte comme si l'annotation `@nospecialize` avait été appliquée. Cette heuristique semble être extrêmement efficace en pratique.

Le problème suivant concerne la structure des tables de hachage du cache de méthode. Des études empiriques montrent que la grande majorité des appels dispatchés dynamiquement impliquent un ou deux arguments. En retour, beaucoup de ces cas peuvent être résolus en considérant uniquement le premier argument. (À part : les partisans du dispatching simple ne seraient pas du tout surpris par cela. Cependant, cet argument signifie "le dispatching multiple est facile à optimiser en pratique", et que nous devrions donc l'utiliser, *pas* "nous devrions utiliser le dispatching simple" !) Ainsi, le cache de méthode utilise le type du premier argument comme clé principale. Notez cependant que cela correspond au *deuxième* élément du type de tuple pour un appel de fonction (le premier élément étant le type de la fonction elle-même). En général, la variation de type en position de tête est extrêmement faible – en effet, la majorité des fonctions appartiennent à des types singleton sans paramètres. Cependant, ce n'est pas le cas pour les constructeurs, où une seule table de méthode contient des constructeurs pour chaque type. Par conséquent, la table de méthode `Type` est traitée de manière spéciale pour utiliser le *premier* élément de type tuple au lieu du second.

Le front end génère des déclarations de type pour toutes les fermetures. Au départ, cela a été mis en œuvre en générant des déclarations de type normales. Cependant, cela a produit un nombre extrêmement élevé de constructeurs, tous trivials (se contentant de passer tous les arguments à [`new`](@ref)). Étant donné que les méthodes sont partiellement ordonnées, l'insertion de toutes ces méthodes est O(n²), de plus, il y en a tout simplement trop pour les garder. Cela a été optimisé en générant directement des expressions `struct_type` (en contournant la génération de constructeur par défaut) et en utilisant `new` directement pour créer des instances de fermeture. Ce n'est pas la chose la plus jolie qui soit, mais on fait ce qu'on doit faire.

Le problème suivant était le macro `@test`, qui générait une fermeture à 0 argument pour chaque cas de test. Ce n'est pas vraiment nécessaire, puisque chaque cas de test est simplement exécuté une fois sur place. Par conséquent, `@test` a été modifié pour s'étendre à un bloc try-catch qui enregistre le résultat du test (vrai, faux ou exception levée) et appelle le gestionnaire de suite de tests à ce sujet.
