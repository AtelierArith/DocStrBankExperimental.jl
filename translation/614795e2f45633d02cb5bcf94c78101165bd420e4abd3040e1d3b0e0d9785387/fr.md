# [Documentation](@id man-documentation)

## Accessing Documentation

La documentation peut être consultée au REPL ou dans [IJulia](https://github.com/JuliaLang/IJulia.jl) en tapant `?` suivi du nom d'une fonction ou d'une macro, puis en appuyant sur `Entrée`. Par exemple,

```julia
?cos
?@time
?r""
```

affichera la documentation pour la fonction, la macro ou la macro de chaîne pertinente respectivement. La plupart des environnements Julia offrent un moyen d'accéder directement à la documentation :

  * [VS Code](https://www.julia-vscode.org/) affiche la documentation lorsque vous survolez un nom de fonction. Vous pouvez également utiliser le panneau Julia dans la barre latérale pour rechercher de la documentation.
  * Dans [Pluto](https://github.com/fonsp/Pluto.jl), ouvrez le panneau "Live Docs" en bas à droite.
  * Dans [Juno](https://junolab.org), en utilisant `Ctrl-J, Ctrl-D`, vous verrez la documentation pour l'objet sous le curseur.

`Docs.hasdoc(module, name)::Bool` indique si un nom a une docstring. `Docs.undocumented_names(module; all)` renvoie les noms non documentés dans un module.

## Writing Documentation

Julia permet aux développeurs de packages et aux utilisateurs de documenter facilement les fonctions, types et autres objets grâce à un système de documentation intégré.

La syntaxe de base est simple : toute chaîne apparaissant juste avant un objet (fonction, macro, type ou instance) sera interprétée comme le documentant (ceci est appelé *docstrings*). Notez qu'aucune ligne vide ou commentaire ne peut intervenir entre un docstring et l'objet documenté. Voici un exemple de base :

```julia
"Tell whether there are too foo items in the array."
foo(xs::Array) = ...
```

La documentation est interprétée comme [Markdown](https://en.wikipedia.org/wiki/Markdown), vous pouvez donc utiliser l'indentation et les blocs de code pour délimiter les exemples de code du texte. Techniquement, tout objet peut être associé à un autre en tant que métadonnées ; Markdown est par défaut, mais on peut également construire d'autres macros de chaîne et les passer à la macro `@doc`.

!!! note
    Le support Markdown est implémenté dans la bibliothèque standard `Markdown` et pour une liste complète de la syntaxe prise en charge, voir le [documentation](@ref markdown_stdlib).


D'accord, je suis prêt à traduire le contenu Markdown que vous allez fournir.

````julia
"""
    bar(x[, y])

Compute the Bar index between `x` and `y`.

If `y` is unspecified, compute the Bar index between all pairs of columns of `x`.

# Examples
```julia-repl
julia> bar([1, 2], [1, 2])
1
```
"""
function bar(x, y) ...
````

Comme dans l'exemple ci-dessus, nous recommandons de suivre quelques conventions simples lors de la rédaction de la documentation :

1. Always show the signature of a function at the top of the documentation, with a four-space indent so that it is printed as Julia code.

    Cela peut être identique à la signature présente dans le code Julia (comme `mean(x::AbstractArray)`), ou une forme simplifiée. Les arguments optionnels doivent être représentés avec leurs valeurs par défaut (c'est-à-dire `f(x, y=1)`) lorsque cela est possible, en suivant la syntaxe Julia réelle. Les arguments optionnels qui n'ont pas de valeur par défaut doivent être mis entre crochets (c'est-à-dire `f(x[, y])` et `f(x[, y[, z]])`). Une solution alternative consiste à utiliser plusieurs lignes : une sans arguments optionnels, l'autre(s) avec eux. Cette solution peut également être utilisée pour documenter plusieurs méthodes liées d'une fonction donnée. Lorsqu'une fonction accepte de nombreux arguments nommés, incluez uniquement un espace réservé `<arguments nommés>` dans la signature (c'est-à-dire `f(x; <arguments nommés>)`), et donnez la liste complète dans une section `# Arguments` (voir point 4 ci-dessous).
2. Inclure une seule phrase en une ligne décrivant ce que fait la fonction ou ce que représente l'objet après le bloc de signature simplifié. Si nécessaire, fournissez plus de détails dans un deuxième paragraphe, après un espace vide.

    La phrase en une ligne doit utiliser la forme impérative ("Faites ceci", "Retournez cela") au lieu de la troisième personne (ne pas écrire "Retourne la longueur...") lors de la documentation des fonctions. Elle doit se terminer par un point. Si le sens d'une fonction ne peut pas être résumé facilement, il pourrait être bénéfique de la diviser en parties composables séparées (cela ne doit pas être considéré comme une exigence absolue pour chaque cas cependant).
3. Ne vous répétez pas.

    Puisque le nom de la fonction est donné par la signature, il n'est pas nécessaire de commencer la documentation par "La fonction `bar`...": allez droit au but. De même, si la signature spécifie les types des arguments, les mentionner dans la description est redondant.
4. Fournissez une liste d'arguments uniquement lorsque cela est vraiment nécessaire.

    Pour les fonctions simples, il est souvent plus clair de mentionner le rôle des arguments directement dans la description de l'objectif de la fonction. Une liste d'arguments ne ferait que répéter des informations déjà fournies ailleurs. Cependant, fournir une liste d'arguments peut être une bonne idée pour des fonctions complexes avec de nombreux arguments (en particulier les arguments de type mot-clé). Dans ce cas, insérez-la après la description générale de la fonction, sous un en-tête `# Arguments`, avec une puce `-` pour chaque argument. La liste doit mentionner les types et les valeurs par défaut (le cas échéant) des arguments :

    ```julia
    """
    ...
    # Arguments
    - `n::Integer`: the number of elements to compute.
    - `dim::Integer=1`: the dimensions along which to perform the computation.
    ...
    """
    ```
5. Fournir des indices sur les fonctions associées.

    Parfois, il existe des fonctions de fonctionnalité connexe. Pour augmenter la découvrabilité, veuillez fournir une courte liste de celles-ci dans un paragraphe `Voir aussi`.

    ```
    See also [`bar!`](@ref), [`baz`](@ref), [`baaz`](@ref).
    ```
6. Include any code examples in an `# Examples` section.

    Les exemples devraient, dans la mesure du possible, être écrits sous forme de *doctests*. Un *doctest* est un bloc de code délimité (voir [Code blocks](@ref)) commençant par ````` ```jldoctest````` et contenant un nombre quelconque d'invites `julia>` accompagnées d'entrées et de sorties attendues qui imitent le REPL de Julia.

    !!! note
        Les doctests sont activés par [`Documenter.jl`](https://github.com/JuliaDocs/Documenter.jl). Pour une documentation plus détaillée, consultez le [manual](https://juliadocs.github.io/Documenter.jl/).


    Par exemple, dans la docstring suivante, une variable `a` est définie et le résultat attendu, tel qu'il apparaît dans un REPL Julia, apparaît ensuite :

    ````julia
    """
    Some nice documentation here.

    # Examples
    ```jldoctest
    julia> a = [1 2; 3 4]
    2×2 Array{Int64,2}:
     1  2
     3  4
    ```
    """
    ````

    !!! warning
        Appeler `rand` et d'autres fonctions liées aux générateurs de nombres aléatoires (RNG) doit être évité dans les doctests car elles ne produiront pas des sorties cohérentes lors de différentes sessions Julia. Si vous souhaitez montrer certaines fonctionnalités liées à la génération de nombres aléatoires, une option consiste à construire explicitement et à initialiser votre propre objet RNG (voir [`Random`](@ref Random-Numbers)) et à le passer aux fonctions que vous testez dans les doctests.

        La taille des mots du système d'exploitation ([`Int32`](@ref) ou [`Int64`](@ref)) ainsi que les différences de séparateurs de chemin (`/` ou `\`) affecteront également la reproductibilité de certains doctests.

        Notez que les espaces dans votre doctest sont significatifs ! Le doctest échouera si vous mal alignez la sortie de l'impression formatée d'un tableau, par exemple.


    Vous pouvez ensuite exécuter `make -C doc doctest=true` pour exécuter tous les doctests dans le Manuel Julia et la documentation de l'API, ce qui garantira que votre exemple fonctionne.

    Pour indiquer que le résultat de sortie est tronqué, vous pouvez écrire `[...]` à la ligne où la vérification doit s'arrêter. Cela est utile pour cacher une trace de pile (qui contient des références non permanentes aux lignes de code julia) lorsque le doctest montre qu'une exception est levée, par exemple :

    ````julia
    ```jldoctest
    julia> div(1, 0)
    ERROR: DivideError: integer division error
    [...]
    ```
    ````

    Les exemples qui ne peuvent pas être testés doivent être écrits dans des blocs de code délimités commençant par ````` ```julia````` afin qu'ils soient correctement mis en évidence dans la documentation générée.

    !!! tip
        Chaque fois que possible, les exemples doivent être **autonomes** et **exécutables** afin que les lecteurs puissent les essayer sans avoir à inclure de dépendances.
7. Utilisez des accents graves pour identifier le code et les équations.

    Les identifiants et extraits de code Julia doivent toujours apparaître entre des backticks ``` ` ``` pour permettre la mise en surbrillance. Les équations dans la syntaxe LaTeX peuvent être insérées entre des doubles backticks ``` `` ```. Utilisez des caractères Unicode plutôt que leur séquence d'échappement LaTeX, c'est-à-dire ``` ``α = 1`` ``` plutôt que ``` ``\\alpha = 1`` ```.
8. Place the starting and ending `"""` characters on lines by themselves.

    Cela signifie, écrivez :

    ```julia
    """
    ...

    ...
    """
    f(x, y) = ...
    ```

    plutôt que :

    ```julia
    """...

    ..."""
    f(x, y) = ...
    ```

    Cela rend plus clair où commencent et se terminent les docstrings.
9. Respectez la limite de longueur de ligne utilisée dans le code environnant.

    Les docstrings sont modifiées en utilisant les mêmes outils que le code. Par conséquent, les mêmes conventions devraient s'appliquer. Il est recommandé que les lignes ne dépassent pas 92 caractères de large.
10. Provide information allowing custom types to implement the function in an `# Implementation` section. These implementation details are intended for developers rather than users, explaining e.g. which functions should be overridden and which functions automatically use appropriate fallbacks. Such details are best kept separate from the main description of the function's behavior.
11. Pour les longues docstrings, envisagez de diviser la documentation avec un en-tête `# Aide étendue`. Le mode d'aide typique n'affichera que le contenu au-dessus de l'en-tête ; vous pouvez accéder à l'aide complète en ajoutant un '?' au début de l'expression (c'est-à-dire "??foo" plutôt que "?foo").

## Functions & Methods

Les fonctions en Julia peuvent avoir plusieurs implémentations, connues sous le nom de méthodes. Bien qu'il soit de bonne pratique que les fonctions génériques aient un seul but, Julia permet aux méthodes d'être documentées individuellement si nécessaire. En général, seule la méthode la plus générique devrait être documentée, ou même la fonction elle-même (c'est-à-dire l'objet créé sans aucune méthode par `function bar end`). Les méthodes spécifiques ne devraient être documentées que si leur comportement diffère de celui des méthodes plus génériques. Dans tous les cas, elles ne devraient pas répéter les informations fournies ailleurs. Par exemple :

```julia
"""
    *(x, y, z...)

Multiplication operator. `x * y * z *...` calls this function with multiple
arguments, i.e. `*(x, y, z...)`.
"""
function *(x, y, z...)
    # ... [implementation sold separately] ...
end

"""
    *(x::AbstractString, y::AbstractString, z::AbstractString...)

When applied to strings, concatenates them.
"""
function *(x::AbstractString, y::AbstractString, z::AbstractString...)
    # ... [insert secret sauce here] ...
end

help?> *
search: * .*

  *(x, y, z...)

  Multiplication operator. x * y * z *... calls this function with multiple
  arguments, i.e. *(x,y,z...).

  *(x::AbstractString, y::AbstractString, z::AbstractString...)

  When applied to strings, concatenates them.
```

Lors de la récupération de la documentation pour une fonction générique, les métadonnées de chaque méthode sont concaténées avec la fonction `catdoc`, qui peut bien sûr être remplacée pour des types personnalisés.

## Advanced Usage

Le macro `@doc` associe son premier argument à son second dans un dictionnaire par module appelé `META`.

Pour faciliter l'écriture de la documentation, le parseur traite le nom de macro `@doc` de manière spéciale : si un appel à `@doc` a un argument, mais qu'une autre expression apparaît après un saut de ligne simple, alors cette expression supplémentaire est ajoutée comme argument à la macro. Par conséquent, la syntaxe suivante est analysée comme un appel à `@doc` avec 2 arguments :

```julia
@doc raw"""
...
"""
f(x) = x
```

Cela permet d'utiliser des expressions autres que des littéraux de chaîne normaux (comme le macro de chaîne `raw""`) en tant que docstring.

Lorsqu'il est utilisé pour récupérer de la documentation, la macro `@doc` (ou, de manière équivalente, la fonction `doc`) recherchera dans tous les dictionnaires `META` les métadonnées pertinentes pour l'objet donné et les renverra. L'objet retourné (un contenu Markdown, par exemple) s'affichera par défaut de manière intelligente. Ce design facilite également l'utilisation du système de documentation de manière programmatique ; par exemple, pour réutiliser la documentation entre différentes versions d'une fonction :

```julia
@doc "..." foo!
@doc (@doc foo!) foo
```

Ou pour une utilisation avec la fonctionnalité de métaprogrammation de Julia :

```julia
for (f, op) in ((:add, :+), (:subtract, :-), (:multiply, :*), (:divide, :/))
    @eval begin
        $f(a, b) = $op(a, b)
    end
end
@doc "`add(a, b)` adds `a` and `b` together" add
@doc "`subtract(a, b)` subtracts `b` from `a`" subtract
```

La documentation dans des blocs non de niveau supérieur, tels que `begin`, `if`, `for`, `let` et les constructeurs internes, doit également être ajoutée au système de documentation via `@doc`. Par exemple :

```julia
if condition()
    @doc "..."
    f(x) = x
end
```

ajoutera de la documentation à `f(x)` lorsque `condition()` est `true`. Notez que même si `f(x)` sort de la portée à la fin d'un bloc, sa documentation restera.

Il est possible d'utiliser la métaprogrammation pour aider à la création de documentation. Lors de l'utilisation de l'interpolation de chaînes dans la docstring, vous devrez utiliser un `$` supplémentaire comme montré avec `$($name)` :

```julia
for func in (:day, :dayofmonth)
    name = string(func)
    @eval begin
        @doc """
            $($name)(dt::TimeType) -> Int64

        The day of month of a `Date` or `DateTime` as an `Int64`.
        """ $func(dt::Dates.TimeType)
    end
end
```

### Dynamic documentation

Parfois, la documentation appropriée pour une instance d'un type dépend des valeurs des champs de cette instance, plutôt que simplement du type lui-même. Dans ces cas, vous pouvez ajouter une méthode à `Docs.getdoc` pour votre type personnalisé qui renvoie la documentation sur une base par instance. Par exemple,

```julia
struct MyType
    value::Int
end

Docs.getdoc(t::MyType) = "Documentation for MyType with value $(t.value)"

x = MyType(1)
y = MyType(2)
```

`?x` affichera "Documentation pour MyType avec la valeur 1" tandis que `?y` affichera "Documentation pour MyType avec la valeur 2".

## Syntax Guide

Ce guide fournit un aperçu complet de la manière d'attacher de la documentation à tous les éléments de syntaxe Julia pour lesquels il est possible de fournir une documentation.

Dans les exemples suivants, `"..."` est utilisé pour illustrer une docstring arbitraire.

### `$` and `\` characters

Les caractères `$` et `\` sont toujours analysés comme une interpolation de chaîne ou le début d'une séquence d'échappement dans les docstrings également. Le macro de chaîne `raw""` associé au macro `@doc` peut être utilisé pour éviter d'avoir à les échapper. Cela est pratique lorsque les docstrings incluent des exemples de code source LaTeX ou Julia contenant de l'interpolation :

````julia
@doc raw"""
```math
\LaTeX
```
"""
function f end
````

### Functions and Methods

```julia
"..."
function f end

"..."
f
```

Ajoute une docstring `"..."` à la fonction `f`. La première version est la syntaxe préférée, cependant les deux sont équivalentes.

```julia
"..."
f(x) = x

"..."
function f(x)
    return x
end

"..."
f(x)
```

Ajoute une docstring `"..."` à la méthode `f(::Any)`.

```julia
"..."
f(x, y = 1) = x + y
```

Ajoute une docstring `"..."` à deux `Method`s, à savoir `f(::Any)` et `f(::Any, ::Any)`.

### Macros

```julia
"..."
macro m(x) end
```

Ajoute la docstring `"..."` à la définition du macro `@m(::Any)`.

```julia
"..."
:(@m1)

"..."
macro m2 end
```

Ajoute la docstring `"..."` aux macros nommées `@m1` et `@m2`.

### Types

```
"..."
abstract type T1 end

"..."
mutable struct T2
    ...
end

"..."
struct T3
    ...
end
```

Ajoute la docstring `"..."` aux types `T1`, `T2` et `T3`.

```
"..."
T1

"..."
T2

"..."
T3
```

Ajoute la docstring `"..."` aux types `T1`, `T2` et `T3`. La version précédente est la syntaxe préférée, cependant les deux sont équivalentes.

```julia
"..."
struct T
    "x"
    x
    "y"
    y

    @doc "Inner constructor"
    function T()
        new(...)
    end
end
```

Ajoute une docstring `"..."` au type `T`, `"x"` au champ `T.x`, `"y"` au champ `T.y`, et `"Constructeur interne"` au constructeur interne `T()`. Également applicable aux types `mutable struct`.

### Modules

```julia
"..."
module M end

module M

"..."
M

end
```

Ajoute une docstring `"..."` au `Module` `M`. Ajouter la docstring au-dessus du `Module` est la syntaxe préférée, cependant les deux sont équivalentes.

```julia
"..."
baremodule M
# ...
end

baremodule M

import Base: @doc

"..."
f(x) = x

end
```

Documenter un `baremodule` en plaçant une chaîne de documentation au-dessus de l'expression importe automatiquement `@doc` dans le module. Ces imports doivent être effectués manuellement lorsque l'expression du module n'est pas documentée.

### Global Variables

```julia
"..."
const a = 1

"..."
b = 2

"..."
global c = 3
```

Ajoute la docstring `"..."` aux `Binding`s `a`, `b` et `c`.

Les `Binding`s sont utilisés pour stocker une référence à un `Symbol` particulier dans un `Module` sans stocker la valeur référencée elle-même.

!!! note
    Lorsque une définition `const` est uniquement utilisée pour définir un alias d'une autre définition, comme c'est le cas avec la fonction `div` et son alias `÷` dans `Base`, ne documentez pas l'alias et documentez plutôt la fonction réelle.

    Si l'alias est documenté et non la véritable définition, alors le système de documentation (`?` mode) ne renverra pas la docstring attachée à l'alias lorsque la véritable définition est recherchée.

    Par exemple, vous devriez écrire

    ```julia
    "..."
    f(x) = x + 1
    const alias = f
    ```

    plutôt que

    ```julia
    f(x) = x + 1
    "..."
    const alias = f
    ```


```julia
"..."
sym
```

Ajoute une docstring `"..."` à la valeur associée à `sym`. Cependant, il est préférable que `sym` soit documenté là où il est défini.

### Multiple Objects

```julia
"..."
a, b
```

Ajoute une docstring `"..."` à `a` et `b`, chacun devant être une expression documentable. Cette syntaxe est équivalente à

```julia
"..."
a

"..."
b
```

Tout nombre d'expressions peut être documenté ensemble de cette manière. Cette syntaxe peut être utile lorsque deux fonctions sont liées, comme les versions non mutantes et mutantes `f` et `f!`.

### Macro-generated code

```julia
"..."
@m expression
```

Ajoute une docstring `"..."` à l'expression générée par l'expansion de `@m expression`. Cela permet aux expressions décorées avec `@inline`, `@noinline`, `@generated`, ou toute autre macro d'être documentées de la même manière que les expressions non décorées.

Les auteurs de macros doivent noter que seules les macros qui génèrent une seule expression prendront automatiquement en charge les docstrings. Si une macro retourne un bloc contenant plusieurs sous-expressions, alors la sous-expression qui doit être documentée doit être marquée en utilisant la macro [`@__doc__`](@ref Core.@__doc__).

Le macro [`@enum`](@ref) utilise `@__doc__` pour permettre la documentation des [`Enum`](@ref). L'examen de sa définition devrait servir d'exemple sur la façon d'utiliser `@__doc__` correctement.

```@docs
Core.@__doc__
```
