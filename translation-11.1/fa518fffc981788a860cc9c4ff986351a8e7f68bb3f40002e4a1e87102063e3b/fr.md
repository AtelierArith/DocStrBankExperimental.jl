# [Modules](@id modules)

Les modules en Julia aident à organiser le code en unités cohérentes. Ils sont délimités syntaxiquement à l'intérieur de `module NomDuModule ... end`, et ont les caractéristiques suivantes :

1. Les modules sont des espaces de noms séparés, chacun introduisant un nouvel espace global. Cela est utile, car cela permet d'utiliser le même nom pour différentes fonctions ou variables globales sans conflit, tant qu'elles se trouvent dans des modules séparés.
2. Les modules disposent de fonctionnalités pour une gestion détaillée des espaces de noms : chacun définit un ensemble de noms qu'il `exporte` et marque comme `public`, et peut importer des noms d'autres modules avec `using` et `import` (nous expliquons cela ci-dessous).
3. Les modules peuvent être précompilés pour un chargement plus rapide et peuvent contenir du code pour l'initialisation à l'exécution.

Typiquement, dans les plus grands paquets Julia, vous verrez le code du module organisé en fichiers, par exemple

```julia
module SomeModule

# export, public, using, import statements are usually here; we discuss these below

include("file1.jl")
include("file2.jl")

end
```

Les fichiers et les noms de fichiers sont principalement sans rapport avec les modules ; les modules ne sont associés qu'aux expressions de module. On peut avoir plusieurs fichiers par module, et plusieurs modules par fichier. `include` se comporte comme si le contenu du fichier source était évalué dans le scope global du module incluant. Dans ce chapitre, nous utilisons des exemples courts et simplifiés, donc nous n'utiliserons pas `include`.

Le style recommandé est de ne pas indenter le corps du module, car cela conduirait généralement à l'indentation de fichiers entiers. De plus, il est courant d'utiliser `UpperCamelCase` pour les noms de modules (tout comme pour les types) et d'utiliser la forme plurielle si applicable, surtout si le module contient un identifiant de nom similaire, afin d'éviter les conflits de noms. Par exemple,

```julia
module FastThings

struct FastThing
    ...
end

end
```

## [Namespace management](@id namespace-management)

La gestion des espaces de noms fait référence aux fonctionnalités que le langage offre pour rendre les noms d'un module disponibles dans d'autres modules. Nous discutons ci-dessous des concepts et des fonctionnalités connexes en détail.

### Qualified names

Les noms des fonctions, des variables et des types dans l'espace global, comme `sin`, `ARGS` et `UnitRange`, appartiennent toujours à un module, appelé le *module parent*, qui peut être trouvé de manière interactive avec [`parentmodule`](@ref), par exemple.

```jldoctest
julia> parentmodule(UnitRange)
Base
```

On peut également se référer à ces noms en dehors de leur module parent en les préfixant avec leur module, par exemple `Base.UnitRange`. Cela s'appelle un *nom qualifié*. Le module parent peut être accessible en utilisant une chaîne de sous-modules comme `Base.Math.sin`, où `Base.Math` est appelé le *chemin du module*. En raison d'ambiguïtés syntaxiques, qualifier un nom qui ne contient que des symboles, comme un opérateur, nécessite d'insérer un deux-points, par exemple `Base.:+`. Un petit nombre d'opérateurs nécessite également des parenthèses, par exemple `Base.:(==)`.

Si un nom est qualifié, alors il est toujours *accessible*, et dans le cas d'une fonction, il peut également avoir des méthodes ajoutées en utilisant le nom qualifié comme nom de fonction.

Dans un module, un nom de variable peut être "réservé" sans lui assigner une valeur en le déclarant comme `global x`. Cela empêche les conflits de noms pour les variables globales initialisées après le temps de chargement. La syntaxe `M.x = y` ne fonctionne pas pour assigner une variable globale dans un autre module ; l'assignation globale est toujours locale au module.

### Export lists

Les noms (se référant aux fonctions, types, variables globales et constantes) peuvent être ajoutés à la *liste d'exportation* d'un module avec `export` : ce sont les symboles qui sont importés lors de l'utilisation du module. En général, ils se trouvent en haut ou près du début de la définition du module afin que les lecteurs du code source puissent les trouver facilement, comme dans

```jldoctest module_manual
julia> module NiceStuff
       export nice, DOG
       struct Dog end      # singleton type, not exported
       const DOG = Dog()   # named instance, exported
       nice(x) = "nice $x" # function, exported
       end;

```

mais ceci n'est qu'une suggestion de style — un module peut avoir plusieurs déclarations `export` à des emplacements arbitraires.

Il est courant d'exporter des noms qui font partie de l'API (interface de programmation d'application). Dans le code ci-dessus, la liste d'exportation suggère que les utilisateurs devraient utiliser `nice` et `DOG`. Cependant, puisque les noms qualifiés rendent toujours les identifiants accessibles, cela n'est qu'une option pour organiser les API : contrairement à d'autres langages, Julia n'a pas de moyens pour cacher véritablement les internes des modules.

Aussi, certains modules n'exportent pas de noms du tout. Cela est généralement fait s'ils utilisent des mots courants, tels que `dérivée`, dans leur API, ce qui pourrait facilement entrer en conflit avec les listes d'exportation d'autres modules. Nous verrons comment gérer les conflits de noms ci-dessous.

Pour marquer un nom comme public sans l'exporter dans l'espace de noms des personnes qui appellent `using NiceStuff`, on peut utiliser `public` au lieu de `export`. Cela marque le(s) nom(s) public(s) comme faisant partie de l'API publique, mais n'a pas d'implications sur l'espace de noms. Le mot-clé `public` n'est disponible qu'à partir de Julia 1.11. Pour maintenir la compatibilité avec Julia 1.10 et les versions antérieures, utilisez la macro `@compat` du package [Compat](https://github.com/JuliaLang/Compat.jl).

### Standalone `using` and `import`

Pour une utilisation interactive, la manière la plus courante de charger un module est `using ModuleName`. Cela [loads](@ref code-loading) le code associé à `ModuleName`, et apporte

1. le nom du module
2. et les éléments de la liste d'exportation dans l'espace de noms global environnant.

Techniquement, l'instruction `using ModuleName` signifie qu'un module appelé `ModuleName` sera disponible pour résoudre les noms au besoin. Lorsqu'une variable globale est rencontrée et qu'elle n'a pas de définition dans le module actuel, le système la recherchera parmi les variables exportées par `ModuleName` et l'utilisera si elle y est trouvée. Cela signifie que toutes les utilisations de cette variable globale dans le module actuel se résoudront à la définition de cette variable dans `ModuleName`.

Pour charger un module à partir d'un package, l'instruction `using ModuleName` peut être utilisée. Pour charger un module à partir d'un module défini localement, un point doit être ajouté avant le nom du module comme `using .ModuleName`.

Pour continuer avec notre exemple,

```jldoctest module_manual
julia> using .NiceStuff
```

charger le code ci-dessus, rendant `NiceStuff` (le nom du module), `DOG` et `nice` disponibles. `Dog` n'est pas sur la liste des exportations, mais il peut être accessible si le nom est qualifié avec le chemin du module (qui ici est juste le nom du module) sous la forme `NiceStuff.Dog`.

Il est important de noter que **`using ModuleName` est la seule forme pour laquelle les listes d'exportation ont de l'importance**.

En revanche,

```jldoctest module_manual
julia> import .NiceStuff
```

apporte *uniquement* le nom du module dans le scope. Les utilisateurs devront utiliser `NiceStuff.DOG`, `NiceStuff.Dog` et `NiceStuff.nice` pour accéder à son contenu. En général, `import ModuleName` est utilisé dans des contextes où l'utilisateur souhaite garder l'espace de noms propre. Comme nous le verrons dans la section suivante, `import .NiceStuff` est équivalent à `using .NiceStuff: NiceStuff`.

Vous pouvez combiner plusieurs déclarations `using` et `import` du même type dans une expression séparée par des virgules, par exemple.

```jldoctest module_manual
julia> using LinearAlgebra, Random
```

### `using` and `import` with specific identifiers, and adding methods

Lorsque `using ModuleName:` ou `import ModuleName:` est suivi d'une liste de noms séparés par des virgules, le module est chargé, mais *seuls ces noms spécifiques sont intégrés dans l'espace de noms* par l'instruction. Par exemple,

```jldoctest module_manual
julia> using .NiceStuff: nice, DOG
```

importer les noms `nice` et `DOG`.

Il est important de noter que le nom du module `NiceStuff` *ne* sera pas dans l'espace de noms. Si vous souhaitez le rendre accessible, vous devez le lister explicitement, comme

```jldoctest module_manual
julia> using .NiceStuff: nice, DOG, NiceStuff
```

Lorsque deux ou plusieurs packages/modules exportent un nom et que ce nom ne fait pas référence à la même chose dans chacun des packages, et que les packages sont chargés via `using` sans une liste explicite de noms, il est alors erroné de référencer ce nom sans qualification. Il est donc recommandé que le code destiné à être compatible avec les futures versions de ses dépendances et de Julia, par exemple, le code dans les packages publiés, liste les noms qu'il utilise de chaque package chargé, par exemple, `using Foo: Foo, f` plutôt que `using Foo`.

Julia a deux formes pour apparemment la même chose car seul `import ModuleName: f` permet d'ajouter des méthodes à `f` *sans un chemin de module*. C'est-à-dire que l'exemple suivant donnera une erreur :

```jldoctest module_manual
julia> using .NiceStuff: nice

julia> struct Cat end

julia> nice(::Cat) = "nice 😸"
ERROR: invalid method definition in Main: function NiceStuff.nice must be explicitly imported to be extended
Stacktrace:
 [1] top-level scope
   @ none:0
 [2] top-level scope
   @ none:1

```

Cette erreur empêche d'ajouter accidentellement des méthodes à des fonctions dans d'autres modules que vous aviez seulement l'intention d'utiliser.

Il y a deux façons de traiter cela. Vous pouvez toujours qualifier les noms de fonction avec un chemin de module :

```jldoctest module_manual
julia> using .NiceStuff

julia> struct Cat end

julia> NiceStuff.nice(::Cat) = "nice 😸"

```

Alternativement, vous pouvez `importer` le nom de la fonction spécifique :

```jldoctest module_manual
julia> import .NiceStuff: nice

julia> struct Cat end

julia> nice(::Cat) = "nice 😸"
nice (generic function with 2 methods)
```

Le choix que vous faites est une question de style. La première forme rend clair que vous ajoutez une méthode à une fonction dans un autre module (rappelez-vous que les imports et la définition de la méthode peuvent être dans des fichiers séparés), tandis que la seconde est plus courte, ce qui est particulièrement pratique si vous définissez plusieurs méthodes.

Une fois qu'une variable est rendue visible via `using` ou `import`, un module ne peut pas créer sa propre variable avec le même nom. Les variables importées sont en lecture seule ; l'assignation à une variable globale affecte toujours une variable appartenant au module actuel, sinon cela soulève une erreur.

### Renaming with `as`

Un identifiant introduit dans le scope par `import` ou `using` peut être renommé avec le mot-clé `as`. Cela est utile pour contourner les conflits de noms ainsi que pour raccourcir les noms. Par exemple, `Base` exporte le nom de fonction `read`, mais le package CSV.jl fournit également `CSV.read`. Si nous allons invoquer la lecture CSV plusieurs fois, il serait pratique de supprimer le qualificateur `CSV.`. Mais alors, il est ambigu de savoir si nous faisons référence à `Base.read` ou `CSV.read` :

```julia-repl
julia> read;

julia> import CSV: read
WARNING: ignoring conflicting import of CSV.read into Main
```

Renommer offre une solution :

```julia-repl
julia> import CSV: read as rd
```

Les packages importés eux-mêmes peuvent également être renommés :

```julia
import BenchmarkTools as BT
```

`as` fonctionne avec `using` uniquement lorsqu'un seul identifiant est mis en portée. Par exemple, `using CSV: read as rd` fonctionne, mais `using CSV as C` ne fonctionne pas, car cela opère sur tous les noms exportés dans `CSV`.

### Mixing multiple `using` and `import` statements

Lorsque plusieurs déclarations `using` ou `import` de l'une des formes ci-dessus sont utilisées, leur effet est combiné dans l'ordre dans lequel elles apparaissent. Par exemple,

```jldoctest module_manual
julia> using .NiceStuff         # exported names and the module name

julia> import .NiceStuff: nice  # allows adding methods to unqualified functions

```

apporterait tous les noms exportés de `NiceStuff` et le nom du module lui-même dans le scope, et permettrait également d'ajouter des méthodes à `nice` sans le préfixer avec un nom de module.

### Handling name conflicts

Considérez la situation où deux (ou plusieurs) packages exportent le même nom, comme dans

```jldoctest module_manual
julia> module A
       export f
       f() = 1
       end
A
julia> module B
       export f
       f() = 2
       end
B
```

L'instruction `using .A, .B` fonctionne, mais lorsque vous essayez d'appeler `f`, vous obtenez une erreur avec un indice.

```jldoctest module_manual
julia> using .A, .B

julia> f
ERROR: UndefVarError: `f` not defined in `Main`
Hint: It looks like two or more modules export different bindings with this name, resulting in ambiguity. Try explicitly importing it from a particular module, or qualifying the name with the module it should come from.
```

Ici, Julia ne peut pas décider de quel `f` vous parlez, donc vous devez faire un choix. Les solutions suivantes sont couramment utilisées :

1. Procédez simplement avec des noms qualifiés comme `A.f` et `B.f`. Cela rend le contexte clair pour le lecteur de votre code, surtout si `f` coïncide par hasard mais a une signification différente dans divers packages. Par exemple, `degré` a diverses utilisations en mathématiques, dans les sciences naturelles et dans la vie quotidienne, et ces significations doivent être gardées séparées.
2. Utilisez le mot-clé `as` ci-dessus pour renommer un ou les deux identifiants, par exemple

    ```jldoctest module_manual
    julia> using .A: f as f

    julia> using .B: f as g

    ```

    rendrait `B.f` disponible sous le nom `g`. Ici, nous supposons que vous n'avez pas utilisé `using A` auparavant, ce qui aurait amené `f` dans l'espace de noms.
3. Lorsque les noms en question *partagent* un sens, il est courant qu'un module l'importe d'un autre, ou qu'il ait un paquet "de base" léger ayant pour seule fonction de définir une interface comme celle-ci, qui peut être utilisée par d'autres paquets. Il est conventionnel que de tels noms de paquets se terminent par `...Base` (ce qui n'a rien à voir avec le module `Base` de Julia).

### Default top-level definitions and bare modules

Les modules contiennent automatiquement `using Core`, `using Base`, et les définitions des fonctions [`eval`](@ref) et [`include`](@ref), qui évaluent des expressions/fichiers dans le scope global de ce module.

Si ces définitions par défaut ne sont pas souhaitées, des modules peuvent être définis en utilisant le mot-clé [`baremodule`](@ref) à la place (note : `Core` est toujours importé). En termes de `baremodule`, un `module` standard ressemble à ceci :

```
baremodule Mod

using Base

eval(x) = Core.eval(Mod, x)
include(p) = Base.include(Mod, p)

...

end
```

Si même `Core` n'est pas souhaité, un module qui n'importe rien et ne définit aucun nom peut être défini avec `Module(:YourNameHere, false, false)` et du code peut y être évalué avec [`@eval`](@ref) ou [`Core.eval`](@ref) :

```jldoctest
julia> arithmetic = Module(:arithmetic, false, false)
Main.arithmetic

julia> @eval arithmetic add(x, y) = $(+)(x, y)
add (generic function with 1 method)

julia> arithmetic.add(12, 13)
25
```

### Standard modules

Il y a trois modules standards importants :

  * [`Core`](@ref) contient toutes les fonctionnalités "intégrées" dans le langage.
  * [`Base`](@ref) contient des fonctionnalités de base qui sont utiles dans presque tous les cas.
  * [`Main`](@ref) est le module de niveau supérieur et le module actuel, lorsque Julia est démarré.

!!! note "Standard library modules"
    Par défaut, Julia est livré avec certains modules de bibliothèque standard. Ceux-ci se comportent comme des paquets Julia réguliers, sauf que vous n'avez pas besoin de les installer explicitement. Par exemple, si vous souhaitez effectuer des tests unitaires, vous pouvez charger la bibliothèque standard `Test` comme suit :

    ```julia
    using Test
    ```


## Submodules and relative paths

Les modules peuvent contenir des *sous-modules*, en imbriquant la même syntaxe `module ... end`. Ils peuvent être utilisés pour introduire des espaces de noms séparés, ce qui peut être utile pour organiser des bases de code complexes. Notez que chaque `module` introduit son propre [scope](@ref scope-of-variables), donc les sous-modules n'héritent pas automatiquement des noms de leur parent.

Il est recommandé que les sous-modules se réfèrent à d'autres modules au sein du module parent englobant (y compris ce dernier) en utilisant des *qualificateurs de module relatifs* dans les déclarations `using` et `import`. Un qualificateur de module relatif commence par un point (`.`), qui correspond au module actuel, et chaque `.` successif mène au parent du module actuel. Cela doit être suivi des modules si nécessaire, et finalement du nom réel à accéder, tous séparés par des `.`.

Considérez l'exemple suivant, où le sous-module `SubA` définit une fonction, qui est ensuite étendue dans son module "frère" :

```jldoctest module_manual
julia> module ParentModule
       module SubA
       export add_D  # exported interface
       const D = 3
       add_D(x) = x + D
       end
       using .SubA  # brings `add_D` into the namespace
       export add_D # export it from ParentModule too
       module SubB
       import ..SubA: add_D # relative path for a “sibling” module
       struct Infinity end
       add_D(x::Infinity) = x
       end
       end;

```

Vous pouvez voir du code dans des packages, qui, dans une situation similaire, utilise

```jldoctest module_manual
julia> import .ParentModule.SubA: add_D

```

Cependant, cela fonctionne via [code loading](@ref code-loading), et donc ne fonctionne que si `ParentModule` est dans un package. Il est préférable d'utiliser des chemins relatifs.

Notez que l'ordre des définitions est également important si vous évaluez des valeurs. Considérez

```julia
module TestPackage

export x, y

x = 0

module Sub
using ..TestPackage
z = y # ERROR: UndefVarError: `y` not defined in `Main`
end

y = 1

end
```

où `Sub` essaie d'utiliser `TestPackage.y` avant qu'il ne soit défini, donc il n'a pas de valeur.

Pour des raisons similaires, vous ne pouvez pas utiliser un ordre cyclique :

```julia
module A

module B
using ..C # ERROR: UndefVarError: `C` not defined in `Main.A`
end

module C
using ..B
end

end
```

## Module initialization and precompilation

Les grands modules peuvent prendre plusieurs secondes à charger car l'exécution de toutes les instructions d'un module implique souvent de compiler une grande quantité de code. Julia crée des caches précompilés du module pour réduire ce temps.

Les fichiers de module précompilés (parfois appelés "fichiers de cache") sont créés et utilisés automatiquement lorsque `import` ou `using` charge un module. Si le(s) fichier(s) de cache n'existent pas encore, le module sera compilé et enregistré pour une réutilisation future. Vous pouvez également appeler manuellement [`Base.compilecache(Base.identify_package("modulename"))`](@ref) pour créer ces fichiers sans charger le module. Les fichiers de cache résultants seront stockés dans le sous-dossier `compiled` de `DEPOT_PATH[1]`. Si rien ne change dans votre système, ces fichiers de cache seront utilisés lorsque vous chargerez le module avec `import` ou `using`.

Les fichiers de cache de précompilation stockent les définitions de modules, de types, de méthodes et de constantes. Ils peuvent également stocker des spécialisations de méthodes et le code généré pour celles-ci, mais cela nécessite généralement que le développeur ajoute des directives explicites [`precompile`](@ref) ou exécute des charges de travail qui forcent la compilation pendant la construction du package.

Cependant, si vous mettez à jour les dépendances du module ou modifiez son code source, le module est automatiquement recompilé lors de l'utilisation de `using` ou `import`. Les dépendances sont des modules qu'il importe, la construction Julia, les fichiers qu'il inclut, ou des dépendances explicites déclarées par [`include_dependency(path)`](@ref) dans le(s) fichier(s) du module.

Pour les dépendances de fichiers chargées par `include`, un changement est déterminé en examinant si la taille du fichier (`fsize`) ou le contenu (condensé en un hachage) est inchangé. Pour les dépendances de fichiers chargées par `include_dependency`, un changement est déterminé en examinant si le temps de modification (`mtime`) est inchangé, ou égal au temps de modification tronqué à la seconde la plus proche (pour tenir compte des systèmes qui ne peuvent pas copier le mtime avec une précision inférieure à la seconde). Il prend également en compte si le chemin vers le fichier choisi par la logique de recherche dans `require` correspond au chemin qui avait créé le fichier de précompilation. Il prend également en compte l'ensemble des dépendances déjà chargées dans le processus actuel et ne recompilera pas ces modules, même si leurs fichiers changent ou disparaissent, afin d'éviter de créer des incompatibilités entre le système en cours d'exécution et le cache de précompilation. Enfin, il prend en compte les changements dans tout [compile-time preferences](@ref preferences).

Si vous savez qu'un module n'est *pas* sûr à précompiler (par exemple, pour l'une des raisons décrites ci-dessous), vous devez mettre `__precompile__(false)` dans le fichier du module (généralement placé en haut). Cela fera en sorte que `Base.compilecache` génère une erreur et que `using` / `import` le charge directement dans le processus actuel, en sautant la précompilation et la mise en cache. Cela empêche également le module d'être importé par tout autre module précompilé.

Vous devez être conscient de certains comportements inhérents à la création de bibliothèques partagées incrémentales qui peuvent nécessiter de la prudence lors de l'écriture de votre module. Par exemple, l'état externe n'est pas préservé. Pour y remédier, séparez explicitement les étapes d'initialisation qui doivent se produire à *l'exécution* des étapes qui peuvent se produire à *la compilation*. À cette fin, Julia vous permet de définir une fonction `__init__()` dans votre module qui exécute toutes les étapes d'initialisation qui doivent se produire à l'exécution. Cette fonction ne sera pas appelée lors de la compilation (`--output-*`). En effet, vous pouvez supposer qu'elle sera exécutée exactement une fois dans la durée de vie du code. Vous pouvez, bien sûr, l'appeler manuellement si nécessaire, mais la norme est de supposer que cette fonction traite de l'état de calcul pour la machine locale, qui n'a pas besoin d'être – ou même ne devrait pas être – capturée dans l'image compilée. Elle sera appelée après le chargement du module dans un processus, y compris si elle est chargée dans une compilation incrémentale (`--output-incremental=yes`), mais pas si elle est chargée dans un processus de compilation complète.

En particulier, si vous définissez une `function __init__()` dans un module, alors Julia appellera `__init__()` immédiatement *après* le chargement du module (par exemple, par `import`, `using` ou `require`) à l'exécution pour la *première* fois (c'est-à-dire que `__init__` n'est appelé qu'une seule fois, et seulement après que toutes les instructions du module ont été exécutées). Comme il est appelé après que le module a été entièrement importé, toutes les sous-modules ou autres modules importés ont leurs fonctions `__init__` appelées *avant* le `__init__` du module englobant.

Deux utilisations typiques de `__init__` consistent à appeler des fonctions d'initialisation à l'exécution de bibliothèques C externes et à initialiser des constantes globales qui impliquent des pointeurs retournés par des bibliothèques externes. Par exemple, supposons que nous appelons une bibliothèque C `libfoo` qui nécessite que nous appelions une fonction d'initialisation `foo_init()` à l'exécution. Supposons également que nous souhaitions définir une constante globale `foo_data_ptr` qui contient la valeur de retour d'une fonction `void *foo_data()` définie par `libfoo` – cette constante doit être initialisée à l'exécution (et non à la compilation) car l'adresse du pointeur changera d'une exécution à l'autre. Vous pourriez accomplir cela en définissant la fonction `__init__` suivante dans votre module :

```julia
const foo_data_ptr = Ref{Ptr{Cvoid}}(0)
function __init__()
    ccall((:foo_init, :libfoo), Cvoid, ())
    foo_data_ptr[] = ccall((:foo_data, :libfoo), Ptr{Cvoid}, ())
    nothing
end
```

Remarquez qu'il est parfaitement possible de définir une variable globale à l'intérieur d'une fonction comme `__init__` ; c'est l'un des avantages d'utiliser un langage dynamique. Mais en en faisant une constante au niveau global, nous pouvons garantir que le type est connu du compilateur et lui permettre de générer un code mieux optimisé. Évidemment, toutes les autres variables globales de votre module qui dépendent de `foo_data_ptr` devraient également être initialisées dans `__init__`.

Les constantes impliquant la plupart des objets Julia qui ne sont pas produits par [`ccall`](@ref) n'ont pas besoin d'être placées dans `__init__` : leurs définitions peuvent être précompilées et chargées à partir de l'image de module mise en cache. Cela inclut des objets compliqués alloués sur le tas comme les tableaux. Cependant, toute routine qui renvoie une valeur de pointeur brut doit être appelée à l'exécution pour que la précompilation fonctionne ([`Ptr`](@ref) les objets se transformeront en pointeurs nuls à moins qu'ils ne soient cachés à l'intérieur d'un objet [`isbits`](@ref)). Cela inclut les valeurs de retour des fonctions Julia [`@cfunction`](@ref) et [`pointer`](@ref).

Les types de dictionnaires et d'ensembles, ou en général tout ce qui dépend de la sortie d'une méthode `hash(key)`, sont un cas plus délicat. Dans le cas courant où les clés sont des nombres, des chaînes de caractères, des symboles, des plages, `Expr`, ou des compositions de ces types (via des tableaux, des tuples, des ensembles, des paires, etc.), elles sont sûres à précompiler. Cependant, pour quelques autres types de clés, tels que `Function` ou `DataType` et des types définis par l'utilisateur génériques où vous n'avez pas défini de méthode `hash`, la méthode `hash` par défaut dépend de l'adresse mémoire de l'objet (via son `objectid`) et peut donc changer d'une exécution à l'autre. Si vous avez l'un de ces types de clés, ou si vous n'êtes pas sûr, pour être prudent, vous pouvez initialiser ce dictionnaire depuis votre fonction `__init__`. Alternativement, vous pouvez utiliser le type de dictionnaire [`IdDict`](@ref), qui est spécialement géré par la précompilation afin qu'il soit sûr à initialiser au moment de la compilation.

Lors de l'utilisation de la précompilation, il est important de garder une distinction claire entre la phase de compilation et la phase d'exécution. Dans ce mode, il sera souvent beaucoup plus évident que Julia est un compilateur qui permet l'exécution de code Julia arbitraire, et non un interpréteur autonome qui génère également du code compilé.

D'autres scénarios de défaillance potentiels connus incluent :

1. Compteurs globaux (par exemple, pour tenter d'identifier de manière unique des objets). Considérez le code suivant :

    ```julia
    mutable struct UniquedById
        myid::Int
        let counter = 0
            UniquedById() = new(counter += 1)
        end
    end
    ```

    bien que l'intention de ce code était de donner à chaque instance un identifiant unique, la valeur du compteur est enregistrée à la fin de la compilation. Tous les usages ultérieurs de ce module compilé de manière incrémentale commenceront à partir de cette même valeur de compteur.

    Notez que `objectid` (qui fonctionne en hachant le pointeur mémoire) présente des problèmes similaires (voir les notes sur l'utilisation de `Dict` ci-dessous).

    Une alternative consiste à utiliser une macro pour capturer [`@__MODULE__`](@ref) et la stocker seule avec la valeur actuelle de `counter`, cependant, il peut être préférable de repenser le code pour ne pas dépendre de cet état global.
2. Les collections associatives (telles que `Dict` et `Set`) doivent être re-hachées dans `__init__`. (À l'avenir, un mécanisme pourrait être fourni pour enregistrer une fonction d'initialisation.)
3. En fonction des effets secondaires à la compilation persistant à travers le temps de chargement. Les exemples incluent : la modification de tableaux ou d'autres variables dans d'autres modules Julia ; le maintien de poignées pour des fichiers ou des dispositifs ouverts ; le stockage de pointeurs vers d'autres ressources système (y compris la mémoire) ;
4. Créer des "copies" accidentelles de l'état global d'un autre module, en le référencant directement au lieu de passer par son chemin de recherche. Par exemple, (dans le scope global) :

    ```julia
    #mystdout = Base.stdout #= will not work correctly, since this will copy Base.stdout into this module =#
    # instead use accessor functions:
    getstdout() = Base.stdout #= best option =#
    # or move the assignment into the runtime:
    __init__() = global mystdout = Base.stdout #= also works =#
    ```

Plusieurs restrictions supplémentaires sont imposées sur les opérations qui peuvent être effectuées lors de la précompilation du code pour aider l'utilisateur à éviter d'autres situations de comportement incorrect :

1. Appel de [`eval`](@ref) pour provoquer un effet secondaire dans un autre module. Cela entraînera également l'émission d'un avertissement lorsque le drapeau de précompilation incrémentale est activé.
2. `global const` déclarations depuis le scope local après le début de `__init__()` (voir l'issue #12010 pour les plans d'ajout d'une erreur pour cela)
3. Remplacer un module est une erreur d'exécution lors d'une précompilation incrémentale.

Quelques autres points à garder à l'esprit :

1. Aucune rechargement de code / invalidation de cache n'est effectué après que des modifications ont été apportées aux fichiers source eux-mêmes (y compris par `Pkg.update`), et aucun nettoyage n'est effectué après `Pkg.rm`.
2. Le comportement de partage de mémoire d'un tableau remodelé est ignoré par la précompilation (chaque vue obtient sa propre copie)
3. S'attendre à ce que le système de fichiers reste inchangé entre le temps de compilation et le temps d'exécution, par exemple [`@__FILE__`](@ref)/`source_path()` pour trouver des ressources à l'exécution, ou le macro `@checked_lib` de BinDeps. Parfois, cela est inévitable. Cependant, lorsque cela est possible, il peut être judicieux de copier les ressources dans le module au moment de la compilation afin qu'elles n'aient pas besoin d'être trouvées à l'exécution.
4. Les objets `WeakRef` et les finalizers ne sont actuellement pas gérés correctement par le sérialiseur (cela sera corrigé dans une prochaine version).
5. Il est généralement préférable d'éviter de capturer des références à des instances d'objets de métadonnées internes tels que `Method`, `MethodInstance`, `MethodTable`, `TypeMapLevel`, `TypeMapEntry` et les champs de ces objets, car cela peut confondre le sérialiseur et ne pas conduire au résultat souhaité. Ce n'est pas nécessairement une erreur de le faire, mais vous devez simplement être préparé à ce que le système essaie de copier certains d'entre eux et de créer une instance unique pour d'autres.

Il est parfois utile, lors du développement de modules, de désactiver la précompilation incrémentielle. Le drapeau de ligne de commande `--compiled-modules={yes|no|existing}` vous permet d'activer ou de désactiver la précompilation des modules. Lorsque Julia est démarré avec `--compiled-modules=no`, les modules sérialisés dans le cache de compilation sont ignorés lors du chargement des modules et des dépendances de modules. Dans certains cas, vous pouvez vouloir charger des modules précompilés existants, mais ne pas en créer de nouveaux. Cela peut être fait en démarrant Julia avec `--compiled-modules=existing`. Un contrôle plus fin est disponible avec `--pkgimages={yes|no|existing}`, qui n'affecte que le stockage du code natif lors de la précompilation. `Base.compilecache` peut toujours être appelé manuellement. L'état de ce drapeau de ligne de commande est transmis à `Pkg.build` pour désactiver le déclenchement automatique de la précompilation lors de l'installation, de la mise à jour et de la construction explicite de packages.

Vous pouvez également déboguer certaines erreurs de précompilation avec des variables d'environnement. Définir `JULIA_VERBOSE_LINKING=true` peut aider à résoudre les échecs de liaison des bibliothèques partagées de code natif compilé. Consultez la partie **Documentation des développeurs** du manuel Julia, où vous trouverez plus de détails dans la section documentant les internals de Julia sous "Images de paquets".
