# [Variables](@id man-variables)

Une variable, en Julia, est un nom associé (ou lié) à une valeur. C'est utile lorsque vous souhaitez stocker une valeur (que vous avez obtenue après des calculs, par exemple) pour une utilisation ultérieure. Par exemple :

```julia-repl
# Assign the value 10 to the variable x
julia> x = 10
10

# Doing math with x's value
julia> x + 1
11

# Reassign x's value
julia> x = 1 + 1
2

# You can assign values of other types, like strings of text
julia> x = "Hello World!"
"Hello World!"
```

Julia fournit un système extrêmement flexible pour nommer les variables. Les noms de variables sont sensibles à la casse et n'ont pas de signification sémantique (c'est-à-dire que le langage ne traitera pas les variables différemment en fonction de leurs noms).

```jldoctest
julia> x = 1.0
1.0

julia> y = -3
-3

julia> Z = "My string"
"My string"

julia> customary_phrase = "Hello world!"
"Hello world!"

julia> UniversalDeclarationOfHumanRightsStart = "人人生而自由，在尊严和权利上一律平等。"
"人人生而自由，在尊严和权利上一律平等。"
```

Les noms Unicode (en encodage UTF-8) sont autorisés :

```jldoctest
julia> δ = 0.00001
1.0e-5

julia> 안녕하세요 = "Hello"
"Hello"
```

Dans le REPL Julia et plusieurs autres environnements d'édition Julia, vous pouvez taper de nombreux symboles mathématiques Unicode en tapant le nom du symbole LaTeX précédé d'un antislash, suivi de tab. Par exemple, le nom de variable `δ` peut être saisi en tapant `\delta`-*tab*, ou même `α̂⁽²⁾` en tapant `\alpha`-*tab*-`\hat`-*tab*-`\^(2)`-*tab*. (Si vous trouvez un symbole quelque part, par exemple dans le code de quelqu'un d'autre, que vous ne savez pas comment taper, l'aide du REPL vous le dira : il suffit de taper `?` puis de coller le symbole.)

Julia vous permettra même de masquer les constantes et fonctions exportées existantes avec des locales (bien que cela ne soit pas recommandé pour éviter d'éventuelles confusions) :

```jldoctest; filter = r"with \d+ methods"
julia> pi = 3
3

julia> pi
3

julia> sqrt = 4
4

julia> length() = 5
length (generic function with 1 method)

julia> Base.length
length (generic function with 79 methods)
```

Cependant, si vous essayez de redéfinir une constante ou une fonction intégrée déjà en usage, Julia vous donnera une erreur :

```jldoctest
julia> pi
π = 3.1415926535897...

julia> pi = 3
ERROR: cannot assign a value to imported variable Base.pi from module Main

julia> sqrt(100)
10.0

julia> sqrt = 4
ERROR: cannot assign a value to imported variable Base.sqrt from module Main
```

## [Allowed Variable Names](@id man-allowed-variable-names)

Les noms de variables doivent commencer par une lettre (A-Z ou a-z), un underscore, ou un sous-ensemble de points de code Unicode supérieurs à 00A0 ; en particulier, [Unicode character categories](https://www.fileformat.info/info/unicode/category/index.htm) Lu/Ll/Lt/Lm/Lo/Nl (lettres), Sc/So (symboles monétaires et autres symboles), et quelques autres caractères similaires à des lettres (par exemple, un sous-ensemble des symboles mathématiques Sm) sont autorisés. Les caractères suivants peuvent également inclure ! et des chiffres (0-9 et d'autres caractères dans les catégories Nd/No), ainsi que d'autres points de code Unicode : diacritiques et autres marques modifiantes (catégories Mn/Mc/Me/Sk), certains connecteurs de ponctuation (catégorie Pc), des primes, et quelques autres caractères.

Les opérateurs comme `+` sont également des identifiants valides, mais sont analysés de manière spéciale. Dans certains contextes, les opérateurs peuvent être utilisés comme des variables ; par exemple, `(+)` fait référence à la fonction d'addition, et `(+) = f` la réaffectera. La plupart des opérateurs infixes Unicode (dans la catégorie Sm), tels que `⊕`, sont analysés comme des opérateurs infixes et sont disponibles pour des méthodes définies par l'utilisateur (par exemple, vous pouvez utiliser `const ⊗ = kron` pour définir `⊗` comme un produit de Kronecker infixe). Les opérateurs peuvent également être suffixés avec des marques de modification, des primes et des indices/superscripts, par exemple `+̂ₐ″` est analysé comme un opérateur infixe avec la même priorité que `+`. Un espace est requis entre un opérateur qui se termine par une lettre d'indice/superscript et un nom de variable suivant. Par exemple, si `+ᵃ` est un opérateur, alors `+ᵃx` doit être écrit comme `+ᵃ x` pour le distinguer de `+ ᵃx` où `ᵃx` est le nom de la variable.

Une classe particulière de noms de variables est celle qui ne contient que des traits de soulignement. Ces identifiants sont en écriture seule. C'est-à-dire qu'ils ne peuvent être assignés à des valeurs, qui sont immédiatement jetées, et leurs valeurs ne peuvent être utilisées de quelque manière que ce soit.

```julia-repl
julia> x, ___ = size([2 2; 1 1])
(2, 2)

julia> y = ___
ERROR: syntax: all-underscore identifiers are write-only and their values cannot be used in expressions

julia> println(___)
ERROR: syntax: all-underscore identifiers are write-only and their values cannot be used in expressions
```

The only explicitly disallowed names for variables are the names of the built-in [Keywords](@ref Keywords):

```julia-repl
julia> else = false
ERROR: syntax: unexpected "else"

julia> try = "No"
ERROR: syntax: unexpected "="
```

Certains caractères Unicode sont considérés comme équivalents dans les identifiants. Différentes manières d'entrer des caractères combinants Unicode (par exemple, des accents) sont traitées comme équivalentes (en particulier, les identifiants Julia sont [NFC](https://en.wikipedia.org/wiki/Unicode_equivalence). Julia inclut également quelques équivalences non standard pour des caractères visuellement similaires et facilement saisis par certaines méthodes de saisie. Les caractères Unicode `ɛ` (U+025B : lettre e ouverte latine minuscule) et `µ` (U+00B5 : signe micro) sont traités comme équivalents aux lettres grecques correspondantes. Le point médian `·` (U+00B7) et le grec [interpunct](https://en.wikipedia.org/wiki/Interpunct) `·` (U+0387) sont tous deux traités comme l'opérateur de point mathématique `⋅` (U+22C5). Le signe moins `−` (U+2212) est traité comme équivalent au signe trait d'union `-` (U+002D).

## [Assignment expressions and assignment versus mutation](@id man-assignment-expressions)

Une affectation `variable = valeur` "lie" le nom `variable` à la `valeur` calculée sur le côté droit, et l'ensemble de l'affectation est traité par Julia comme une expression égale à la `valeur` du côté droit. Cela signifie que les affectations peuvent être *chaînées* (la même `valeur` assignée à plusieurs variables avec `variable1 = variable2 = valeur`) ou utilisées dans d'autres expressions, et c'est aussi pourquoi leur résultat est affiché dans le REPL comme la valeur du côté droit. (En général, le REPL affiche la valeur de toute expression que vous évaluez.) Par exemple, ici la valeur `4` de `b = 2+2` est utilisée dans une autre opération arithmétique et affectation :

```jldoctest
julia> a = (b = 2+2) + 3
7

julia> a
7

julia> b
4
```

Une confusion courante est la distinction entre *assignation* (donner un nouveau "nom" à une valeur) et *mutation* (changer une valeur). Si vous exécutez `a = 2` suivi de `a = 3`, vous avez changé le "nom" `a` pour qu'il fasse référence à une nouvelle valeur `3`… vous n'avez pas changé le nombre `2`, donc `2+2` donnera toujours `4` et non `6` ! Cette distinction devient plus claire lorsqu'on traite des types *mutables* comme [arrays](@ref lib-arrays), dont le contenu *peut* être changé :

```jldoctest mutation_vs_rebind
julia> a = [1,2,3] # an array of 3 integers
3-element Vector{Int64}:
 1
 2
 3

julia> b = a   # both b and a are names for the same array!
3-element Vector{Int64}:
 1
 2
 3
```

Ici, la ligne `b = a` ne fait *pas* une copie du tableau `a`, elle lie simplement le nom `b` au *même* tableau `a` : à la fois `b` et `a` "pointent" vers un tableau `[1,2,3]` en mémoire. En revanche, une affectation `a[i] = value` *modifie* le *contenu* du tableau, et le tableau modifié sera visible à travers les deux noms `a` et `b` :

```jldoctest mutation_vs_rebind
julia> a[1] = 42     # change the first element
42

julia> a = 3.14159   # a is now the name of a different object
3.14159

julia> b   # b refers to the original array object, which has been mutated
3-element Vector{Int64}:
 42
  2
  3
```

That is, `a[i] = value` (an alias for [`setindex!`](@ref)) *mutates* an existing array object in memory, accessible via either `a` or `b`.  Subsequently setting `a = 3.14159` does not change this array, it simply binds `a` to a different object; the array is still accessible via `b`. Another common syntax to mutate an existing object is `a.field = value` (an alias for [`setproperty!`](@ref)), which can be used to change a [`mutable struct`](@ref).  There is also mutation via dot assignment, for example `b .= 5:7` (which mutates our array `b` in-place to contain `[5,6,7]`), as part of Julia's [vectorized "dot" syntax](@ref man-dot-operators).

Lorsque vous appelez un [function](@ref man-functions) en Julia, il se comporte comme si vous *aviez assigné* les valeurs des arguments à de nouveaux noms de variables correspondant aux arguments de la fonction, comme discuté dans [Argument-Passing Behavior](@ref man-argument-passing).  (Par [convention](@ref man-punctuation), les fonctions qui modifient un ou plusieurs de leurs arguments ont des noms se terminant par `!`.)

## Stylistic Conventions

Bien que Julia impose peu de restrictions sur les noms valides, il est devenu utile d'adopter les conventions suivantes :

  * Les noms des variables sont en minuscules.
  * La séparation des mots peut être indiquée par des traits de soulignement (`'_'`), mais l'utilisation de traits de soulignement est déconseillée à moins que le nom ne soit difficile à lire autrement.
  * Les noms des `Type`s et `Module`s commencent par une lettre majuscule et la séparation des mots est indiquée par le camel case au lieu des underscores.
  * Les noms des `function`s et `macro`s sont en minuscules, sans underscores.
  * Les fonctions qui écrivent dans leurs arguments ont des noms se terminant par `!`. Celles-ci sont parfois appelées fonctions "mutantes" ou "in-place" car elles sont destinées à produire des changements dans leurs arguments après l'appel de la fonction, et non simplement à retourner une valeur.

Pour plus d'informations sur les conventions stylistiques, voir le [Style Guide](@ref).
