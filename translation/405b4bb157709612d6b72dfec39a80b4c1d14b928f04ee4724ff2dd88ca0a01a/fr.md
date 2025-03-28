# Julia ASTs

Julia a deux représentations de code. D'abord, il y a un AST de syntaxe de surface retourné par le parseur (par exemple, la fonction [`Meta.parse`](@ref)), et manipulé par des macros. C'est une représentation structurée du code tel qu'il est écrit, construite par `julia-parser.scm` à partir d'un flux de caractères. Ensuite, il y a une forme abaissée, ou IR (représentation intermédiaire), qui est utilisée par l'inférence de types et la génération de code. Dans la forme abaissée, il y a moins de types de nœuds, toutes les macros sont développées, et tout le flux de contrôle est converti en branches explicites et séquences d'instructions. La forme abaissée est construite par `julia-syntax.scm`.

Tout d'abord, nous nous concentrerons sur l'AST, car il est nécessaire pour écrire des macros.

## Surface syntax AST

Les ASTs front-end consistent presque entièrement de [`Expr`](@ref) et d'atomes (par exemple, des symboles, des nombres). Il y a généralement une tête d'expression différente pour chaque forme syntaxique visuellement distincte. Des exemples seront donnés en syntaxe s-expression. Chaque liste parenthésée correspond à un Expr, où le premier élément est la tête. Par exemple, `(call f x)` correspond à `Expr(:call, :f, :x)` en Julia.

### Calls

| Input            | AST                                |
|:---------------- |:---------------------------------- |
| `f(x)`           | `(call f x)`                       |
| `f(x, y=1, z=2)` | `(call f x (kw y 1) (kw z 2))`     |
| `f(x; y=1)`      | `(call f (parameters (kw y 1)) x)` |
| `f(x...)`        | `(call f (... x))`                 |

`do` syntax :

```julia
f(x) do a,b
    body
end
```

analyse comme `(do (call f x) (-> (tuple a b) (block body)))`.

### Operators

La plupart des utilisations des opérateurs ne sont que des appels de fonction, ils sont donc analysés avec le préfixe `call`. Cependant, certains opérateurs sont des formes spéciales (pas nécessairement des appels de fonction), et dans ces cas, l'opérateur lui-même est le préfixe de l'expression. Dans julia-parser.scm, ceux-ci sont appelés "opérateurs syntaxiques". Certains opérateurs (`+` et `*`) utilisent une analyse N-aire ; les appels chaînés sont analysés comme un seul appel à N arguments. Enfin, les chaînes de comparaisons ont leur propre structure d'expression spéciale.

| Input       | AST                       |
|:----------- |:------------------------- |
| `x+y`       | `(call + x y)`            |
| `a+b+c+d`   | `(call + a b c d)`        |
| `2x`        | `(call * 2 x)`            |
| `a&&b`      | `(&& a b)`                |
| `x += 1`    | `(+= x 1)`                |
| `a ? 1 : 2` | `(if a 1 2)`              |
| `a,b`       | `(tuple a b)`             |
| `a==b`      | `(call == a b)`           |
| `1<i<=n`    | `(comparison 1 < i <= n)` |
| `a.b`       | `(. a (quote b))`         |
| `a.(b)`     | `(. a (tuple b))`         |

### Bracketed forms

| Input                    | AST                                             |
|:------------------------ |:----------------------------------------------- |
| `a[i]`                   | `(ref a i)`                                     |
| `t[i;j]`                 | `(typed_vcat t i j)`                            |
| `t[i j]`                 | `(typed_hcat t i j)`                            |
| `t[a b; c d]`            | `(typed_vcat t (row a b) (row c d))`            |
| `t[a b;;; c d]`          | `(typed_ncat t 3 (row a b) (row c d))`          |
| `a{b}`                   | `(curly a b)`                                   |
| `a{b;c}`                 | `(curly a (parameters c) b)`                    |
| `[x]`                    | `(vect x)`                                      |
| `[x,y]`                  | `(vect x y)`                                    |
| `[x;y]`                  | `(vcat x y)`                                    |
| `[x y]`                  | `(hcat x y)`                                    |
| `[x y; z t]`             | `(vcat (row x y) (row z t))`                    |
| `[x;y;; z;t;;;]`         | `(ncat 3 (nrow 2 (nrow 1 x y) (nrow 1 z t)))`   |
| `[x for y in z, a in b]` | `(comprehension (generator x (= y z) (= a b)))` |
| `T[x for y in z]`        | `(typed_comprehension T (generator x (= y z)))` |
| `(a, b, c)`              | `(tuple a b c)`                                 |
| `(a; b; c)`              | `(block a b c)`                                 |

### Macros

| Input         | AST                                          |
|:------------- |:-------------------------------------------- |
| `@m x y`      | `(macrocall @m (line) x y)`                  |
| `Base.@m x y` | `(macrocall (. Base (quote @m)) (line) x y)` |
| `@Base.m x y` | `(macrocall (. Base (quote @m)) (line) x y)` |

### Strings

| Input           | AST                                 |
|:--------------- |:----------------------------------- |
| `"a"`           | `"a"`                               |
| `x"y"`          | `(macrocall @x_str (line) "y")`     |
| `x"y"z`         | `(macrocall @x_str (line) "y" "z")` |
| `"x = $x"`      | `(string "x = " x)`                 |
| ``` `a b c` ``` | `(macrocall @cmd (line) "a b c")`   |

Syntax de la chaîne de documentation :

```julia
"some docs"
f(x) = x
```

analyse comme `(macrocall (|.| Core '@doc) (line) "some docs" (= (call f x) (block x)))`.

### Imports and such

| Input               | AST                                 |
|:------------------- |:----------------------------------- |
| `import a`          | `(import (. a))`                    |
| `import a.b.c`      | `(import (. a b c))`                |
| `import ...a`       | `(import (. . . . a))`              |
| `import a.b, c.d`   | `(import (. a b) (. c d))`          |
| `import Base: x`    | `(import (: (. Base) (. x)))`       |
| `import Base: x, y` | `(import (: (. Base) (. x) (. y)))` |
| `export a, b`       | `(export a b)`                      |

`using` a la même représentation que `import`, mais avec l'en-tête d'expression `:using` au lieu de `:import`.

### Numbers

Julia prend en charge plus de types de nombres que de nombreuses implémentations de scheme, donc tous les nombres ne sont pas représentés directement comme des nombres scheme dans l'AST.

| Input                   | AST                                                      |
|:----------------------- |:-------------------------------------------------------- |
| `11111111111111111111`  | `(macrocall @int128_str nothing "11111111111111111111")` |
| `0xfffffffffffffffff`   | `(macrocall @uint128_str nothing "0xfffffffffffffffff")` |
| `1111...many digits...` | `(macrocall @big_str nothing "1111....")`                |

### Block forms

Un bloc d'instructions est analysé comme `(block stmt1 stmt2 ...)`.

Si déclaration :

```julia
if a
    b
elseif c
    d
else
    e
end
```

parses comme :

```
(if a (block (line 2) b)
    (elseif (block (line 3) c) (block (line 4) d)
            (block (line 6 e))))
```

Une boucle `while` se parse comme `(while condition corps)`.

Une boucle `for` se parse comme `(for (= var iter) body)`. S'il y a plus d'une spécification d'itération, elles sont analysées comme un bloc : `(for (block (= v1 iter1) (= v2 iter2)) body)`.

`break` et `continue` sont analysés comme des expressions à 0 argument `(break)` et `(continue)`.

`let` est analysé comme `(let (= var val) corps)` ou `(let (bloc (= var1 val1) (= var2 val2) ...) corps)`, comme les boucles `for`.

Une définition de fonction de base est analysée comme `(function (call f x) body)`. Un exemple plus complexe :

```julia
function f(x::T; k = 1) where T
    return x+1
end
```

parses comme :

```
(function (where (call f (parameters (kw k 1))
                       (:: x T))
                 T)
          (block (line 2) (return (call + x 1))))
```

Définition de type :

```julia
mutable struct Foo{T<:S}
    x::T
end
```

parses comme :

```
(struct true (curly Foo (<: T S))
        (block (line 2) (:: x T)))
```

Le premier argument est un booléen indiquant si le type est mutable.

`try` blocs se analysent comme `(try try_block var catch_block finally_block)`. S'il n'y a pas de variable présente après `catch`, `var` est `#f`. S'il n'y a pas de clause `finally`, alors le dernier argument n'est pas présent.

### Quote expressions

Les formes de syntaxe source de Julia pour le code de citation (`quote` et `:( )`) prennent en charge l'interpolation avec `$`. En termes de Lisp, cela signifie qu'elles sont en réalité des formes de "backquote" ou de "quasiquote". En interne, il existe également un besoin de citation de code sans interpolation. Dans le code de schéma de Julia, la citation non interpolante est représentée par l'en-tête d'expression `inert`.

Les expressions `inert` sont converties en objets `QuoteNode` de Julia. Ces objets enveloppent une seule valeur de n'importe quel type et, lorsqu'ils sont évalués, renvoient simplement cette valeur.

Une expression `quote` dont l'argument est un atome est également convertie en un `QuoteNode`.

### Line numbers

Les informations de localisation source sont représentées sous la forme `(ligne line_num nom_fichier)` où le troisième composant est optionnel (et omis lorsque le numéro de ligne actuel, mais pas le nom de fichier, change).

Ces expressions sont représentées comme des `LineNumberNode`s en Julia.

### Macros

L'hygiène des macros est représentée par l'expression de paire de têtes `escape` et `hygienic-scope`. Le résultat d'une expansion de macro est automatiquement enveloppé dans `(hygienic-scope block module)`, pour représenter le résultat du nouveau scope. L'utilisateur peut insérer `(escape block)` à l'intérieur pour interpoler du code de l'appelant.

## Lowered form

La forme abaissée (IR) est plus importante pour le compilateur, car elle est utilisée pour l'inférence de type, les optimisations comme l'inlining et la génération de code. Elle est également moins évidente pour l'humain, car elle résulte d'un réarrangement significatif de la syntaxe d'entrée.

En plus des `Symbol`s et de certains types de nombres, les types de données suivants existent sous une forme réduite :

  * `Expr`

    A un type de nœud indiqué par le champ `head`, et un champ `args` qui est un `Vector{Any}` de sous-expressions. Bien que presque chaque partie d'un AST de surface soit représentée par un `Expr`, l'IR n'utilise qu'un nombre limité d'`Expr`s, principalement pour les appels et certaines formes réservées au niveau supérieur.
  * `NuméroDeSlot`

    Identifie les arguments et les variables locales par un numérotage consécutif. Il a un champ `id` de type entier donnant l'index de l'emplacement. Les types de ces emplacements peuvent être trouvés dans le champ `slottypes` de leur objet `CodeInfo`.
  * `Argument`

    Le même que `SlotNumber`, mais apparaît uniquement après optimisation. Indique que le slot référencé est un argument de la fonction englobante.
  * `CodeInfo`

    Enveloppe l'IR d'un groupe d'instructions. Son champ `code` est un tableau d'expressions à exécuter.
  * `AllerAuNoeud`

    Branche inconditionnelle. L'argument est la cible de la branche, représentée comme un index dans le tableau de code vers lequel sauter.
  * `GotoIfNot`

    Branche conditionnelle. Si le champ `cond` évalue à faux, va à l'index identifié par le champ `dest`.
  * `ReturnNode`

    Renvoie son argument (le champ `val`) comme valeur de la fonction englobante. Si le champ `val` est indéfini, cela représente une instruction inaccessibile.
  * `QuoteNode`

    Enveloppe une valeur arbitraire pour la référencer en tant que donnée. Par exemple, la fonction `f() = :a` contient un `QuoteNode` dont le champ `value` est le symbole `a`, afin de retourner le symbole lui-même au lieu de l'évaluer.
  * `GlobalRef`

    Fait référence à la variable globale `name` dans le module `mod`.
  * `SSAValue`

    Fait référence à une variable d'affectation unique statique (SSA) numérotée consécutivement (commençant à 1) insérée par le compilateur. Le numéro (`id`) d'un `SSAValue` est l'index du tableau de code de l'expression dont il représente la valeur.
  * `NouveauNoeudVar`

    Marque un point où une variable (emplacement) est créée. Cela a pour effet de réinitialiser une variable à indéfini.

### `Expr` types

Ces symboles apparaissent dans le champ `head` de [`Expr`](@ref) sous forme minuscule.

  * `appel`

    Appel de fonction (dispatch dynamique). `args[1]` est la fonction à appeler, `args[2:end]` sont les arguments.
  * `invoquer`

    Appel de fonction (dispatch statique). `args[1]` est l'instance de méthode à appeler, `args[2:end]` sont les arguments (y compris la fonction qui est appelée, à `args[2]`).
  * `paramètre_statique`

    Référencer un paramètre statique par index.
  * `=`

    Attribution. Dans l'IR, le premier argument est toujours un `SlotNumber` ou un `GlobalRef`.
  * `méthode`

    Ajoute une méthode à une fonction générique et assigne le résultat si nécessaire.

    A une forme à 1 argument et une forme à 3 arguments. La forme à 1 argument découle de la syntaxe `function foo end`. Dans la forme à 1 argument, l'argument est un symbole. Si ce symbole nomme déjà une fonction dans le scope actuel, rien ne se passe. Si le symbole est indéfini, une nouvelle fonction est créée et assignée à l'identifiant spécifié par le symbole. Si le symbole est défini mais nomme un non-fonction, une erreur est levée. La définition de "nomme une fonction" est que la liaison est constante et fait référence à un objet de type singleton. La raison de cela est qu'une instance d'un type singleton identifie de manière unique le type auquel ajouter la méthode. Lorsque le type a des champs, il ne serait pas clair si la méthode était ajoutée à l'instance ou à son type.

    La forme à 3 arguments a les arguments suivants :

      * `args[1]`

        Un nom de fonction, ou `rien` si inconnu ou non nécessaire. S'il s'agit d'un symbole, alors l'expression se comporte d'abord comme la forme à 1 argument ci-dessus. Cet argument est ignoré par la suite. Il peut être `rien` lorsque des méthodes sont ajoutées strictement par type, `(::T)(x) = x`, ou lorsqu'une méthode est ajoutée à une fonction existante, `MyModule.f(x) = x`.
      * `args[2]`

        Un `SimpleVector` de type d'argument de données. `args[2][1]` est un `SimpleVector` des types d'arguments, et `args[2][2]` est un `SimpleVector` de variables de type correspondant aux paramètres statiques de la méthode.
      * `args[3]`

        Un `CodeInfo` de la méthode elle-même. Pour les définitions de méthode "hors de portée" (ajout d'une méthode à une fonction qui a également des méthodes définies dans différentes portées), il s'agit d'une expression qui évalue à une expression `:lambda`.
  * `type_de_structure`

    Une expression à 7 arguments qui définit une nouvelle `struct` :

      * `args[1]`

        Le nom de la `struct`
      * `args[2]`

        Une expression `call` qui crée un `SimpleVector` en spécifiant ses paramètres
      * `args[3]`

        Une expression `call` qui crée un `SimpleVector` en spécifiant ses noms de champ
      * `args[4]`

        Un `Symbol`, `GlobalRef` ou `Expr` spécifiant le supertype (par exemple, `:Integer`, `GlobalRef(Core, :Any)` ou `:(Core.apply_type(AbstractArray, T, N))`)
      * `args[5]`

        Une expression `call` qui crée un `SimpleVector` en spécifiant ses types de champ.
      * `args[6]`

        Un Bool, vrai si `mutable`
      * `args[7]`

        Le nombre d'arguments à initialiser. Ce sera le nombre de champs, ou le nombre minimum de champs appelés par l'instruction `new` d'un constructeur interne.
  * `type_abstrait`

    Une expression à 3 arguments qui définit un nouveau type abstrait. Les arguments sont les mêmes que les arguments 1, 2 et 4 des expressions `struct_type`.
  * `type_primitif`

    Une expression à 4 arguments qui définit un nouveau type primitif. Les arguments 1, 2 et 4 sont les mêmes que `struct_type`. L'argument 3 est le nombre de bits.

    !!! compat "Julia 1.5"
        `struct_type`, `abstract_type` et `primitive_type` ont été supprimés dans Julia 1.5 et remplacés par des appels à de nouveaux builtins.
  * `global`

    Déclare une liaison globale.
  * `const`

    Déclare une variable (globale) comme constante.
  * `nouveau`

    Alloue un nouvel objet de type struct. Le premier argument est le type. La pseudo-fonction [`new`](@ref) est réduite à cela, et le type est toujours inséré par le compilateur. C'est une fonctionnalité très interne, et ne fait aucune vérification. Évaluer des expressions `new` arbitraires peut facilement provoquer un segfault.
  * `splatnew`

    Semblable à `new`, sauf que les valeurs des champs sont passées sous forme d'un seul tuple. Fonctionne de manière similaire à `splat(new)` si `new` était une fonction de première classe, d'où le nom.
  * `estdéfini`

    `Expr(:isdefined, :x)` renvoie un Bool indiquant si `x` a déjà été défini dans le scope actuel.
  * `l_exception`

    Renvoie l'exception capturée à l'intérieur d'un bloc `catch`, telle que retournée par `jl_current_exception(ct)`.
  * `entrer`

    Entrée dans un gestionnaire d'exception (`setjmp`). `args[1]` est l'étiquette du bloc catch vers lequel sauter en cas d'erreur. Produit un jeton qui est consommé par `pop_exception`.
  * `laisser`

    Pop les gestionnaires d'exceptions. `args[1]` est le nombre de gestionnaires à retirer.
  * `pop_exception`

    Renvoyer la pile des exceptions actuelles à l'état associé à `enter` lors de la sortie d'un bloc catch. `args[1]` contient le jeton de l'`enter` associé.

    !!! compat "Julia 1.1"
        `pop_exception` est nouveau dans Julia 1.1.
  * `inbounds`

    Contrôle l'activation ou la désactivation des vérifications de limites. Une pile est maintenue ; si le premier argument de cette expression est vrai ou faux (`true` signifie que les vérifications de limites sont désactivées), il est empilé. Si le premier argument est `:pop`, la pile est dépilée.
  * `boundscheck`

    A la valeur `false` si elle est intégrée dans une section de code marquée avec `@inbounds`, sinon elle a la valeur `true`.
  * `loopinfo`

    Marque la fin d'une boucle. Contient des métadonnées qui sont transmises à `LowerSimdLoop` pour soit marquer la boucle interne de l'expression `@simd`, soit pour propager des informations aux passes de boucle LLVM.
  * `copyast`

    Partie de l'implémentation du quasi-citation. L'argument est un AST de syntaxe de surface qui est simplement copié récursivement et retourné à l'exécution.
  * `meta`

    Métadonnées. `args[1]` est généralement un symbole spécifiant le type de métadonnées, et le reste des arguments est libre. Les types de métadonnées suivants sont couramment utilisés :

      * `:inline` et `:noinline` : Indications d'inlining.
  * `appelétranger`

    Conteneur statiquement calculé pour les informations `ccall`. Les champs sont :

      * `args[1]` : nom

        L'expression qui sera analysée pour la fonction étrangère.
      * `args[2]::Type` : RT

        Le type de retour (littéral), calculé statiquement lorsque la méthode contenant a été définie.
      * `args[3]::SimpleVector` (de Types) : AT

        Le vecteur (littéral) des types d'arguments, calculé statiquement lorsque la méthode contenant a été définie.
      * `args[4]::Int` : nreq

        Le nombre d'arguments requis pour une définition de fonction varargs.
      * `args[5]::QuoteNode{Symbol}` : convention d'appel

        La convention d'appel pour l'appel.
      * `args[6:5+length(args[3])]` : arguments

        Les valeurs pour tous les arguments (avec les types de chacun donnés dans args[3]).
      * `args[6+length(args[3])+1:end]` : racines-gc

        Les objets supplémentaires qui peuvent devoir être gc-rooted pendant la durée de l'appel. Voir [Working with LLVM](@ref Working-with-LLVM) pour savoir d'où ils proviennent et comment ils sont gérés.
  * `new_opaque_closure`

    Construit une nouvelle fermeture opaque. Les champs sont :

      * `args[1]` : signature

        La signature de fonction de la fermeture opaque. Les fermetures opaques ne participent pas à la dispatch, mais les types d'entrée peuvent être restreints.
      * `args[2]` : isva

        Indique si la fermeture accepte des varargs.
      * `args[3]` : lb

        Borne inférieure sur le type de sortie. (Par défaut `Union{}`)
      * `args[4]` : ub

        Limite supérieure sur le type de sortie. (Par défaut `Any`)
      * `args[5]` : méthode

        La méthode réelle en tant qu'expression `opaque_closure_method`.
      * `args[6:end]` : captures

        Les valeurs capturées par la fermeture opaque.

    !!! compat "Julia 1.7"
        Les fermetures opaques ont été ajoutées dans Julia 1.7

### [Method](@id ast-lowered-method)

Un conteneur unique décrivant les métadonnées partagées pour une seule méthode.

  * `nom`, `module`, `fichier`, `ligne`, `sig`

    Métadonnées pour identifier de manière unique la méthode pour l'ordinateur et l'humain.
  * `ambig`

    Cache d'autres méthodes qui peuvent être ambiguës avec celle-ci.
  * `spécialisations`

    Cache de toutes les instances de méthode jamais créées pour cette méthode, utilisé pour garantir l'unicité. L'unicité est requise pour l'efficacité, en particulier pour la précompilation incrémentielle et le suivi de l'invalidation des méthodes.
  * `source`

    Le code source original (si disponible, généralement compressé).
  * `générateur`

    Un objet appelable qui peut être exécuté pour obtenir une source spécialisée pour une signature de méthode spécifique.
  * `racines`

    Pointeurs vers des éléments non-AST qui ont été interpolés dans l'AST, requis par la compression de l'AST, l'inférence de type ou la génération de code natif.
  * `nargs`, `isva`, `appelé`, `is_for_opaque_closure`,

    Des champs de bits descriptifs pour le code source de cette méthode.
  * `monde_principal`

    L'âge du monde qui "possède" cette méthode.

### MethodInstance

Un conteneur unique décrivant une seule signature appelable pour une méthode. Voir en particulier [Proper maintenance and care of multi-threading locks](@ref Proper-maintenance-and-care-of-multi-threading-locks) pour des détails importants sur la façon de modifier ces champs en toute sécurité.

  * `typesDeSpec`

    La clé primaire pour cette MethodInstance. L'unicité est garantie par une recherche `def.specializations`.
  * `def`

    Le `Méthode` que cette fonction décrit est une spécialisation de. Ou un `Module`, si c'est un Lambda de niveau supérieur développé dans un Module, et qui ne fait pas partie d'une Méthode.
  * `sparam_vals`

    Les valeurs des paramètres statiques dans `specTypes`. Pour le `MethodInstance` à `Method.unspecialized`, il s'agit du `SimpleVector` vide. Mais pour un `MethodInstance` à l'exécution provenant du cache `MethodTable`, cela sera toujours défini et indexable.
  * `non inféré`

    Le code source non compressé pour un thunk de niveau supérieur. De plus, pour une fonction générée, c'est l'un des nombreux endroits où le code source peut être trouvé.
  * `arêtes de retour`

    Nous stockons la liste inversée des dépendances de cache pour un suivi efficace du travail de réanalyse/recompilation incrémental qui peut être nécessaire après de nouvelles définitions de méthode. Cela fonctionne en maintenant une liste des autres `MethodInstance` qui ont été inférées ou optimisées pour contenir un appel possible à cette `MethodInstance`. Ces résultats d'optimisation peuvent être stockés quelque part dans le `cache`, ou cela peut avoir été le résultat de quelque chose que nous ne voulions pas mettre en cache, comme la propagation de constantes. Ainsi, nous fusionnons tous ces arrières de bord vers diverses entrées de cache ici (il n'y a presque toujours qu'une seule entrée de cache applicable avec une valeur sentinelle pour max_world de toute façon).
  * `cache`

    Cache des objets `CodeInstance` qui partagent cette instanciation de modèle.

### CodeInstance

  * `def`

    L'`InstanceMéthode` dont cette entrée de cache est dérivée.
  * `propriétaire`

    Un jeton qui représente le propriétaire de cette `CodeInstance`. Utilisera `jl_egal` pour faire correspondre.

  * `rettype`/`rettype_const`

    Le type de retour inféré pour le champ `specFunctionObject`, qui (dans la plupart des cas) est également le type de retour calculé pour la fonction en général.
  * `inféré`

    Peut contenir un cache de la source inférée pour cette fonction, ou il pourrait être défini sur `rien` pour simplement indiquer que `rettype` est inféré.
  * `ftpr`

    Le point d'entrée générique jlcall.
  * `jlcall_api`

    L'ABI à utiliser lors de l'appel de `fptr`. Certains d'entre eux incluent :

      * 0 - Pas encore compilé
      * 1 - `JL_CALLABLE` `jl_value_t *(*)(jl_function_t *f, jl_value_t *args[nargs], uint32_t nargs)`
      * 2 - Constante (valeur stockée dans `rettype_const`)
      * 3 - Avec des paramètres statiques transmis `jl_value_t *(*)(jl_svec_t *sparams, jl_function_t *f, jl_value_t *args[nargs], uint32_t nargs)`
      * 4 - Exécuter dans l'interpréteur `jl_value_t *(*)(jl_method_instance_t *meth, jl_function_t *f, jl_value_t *args[nargs], uint32_t nargs)`
  * `min_monde` / `max_monde`

    La plage des âges du monde pour laquelle cette instance de méthode est valide à appeler. Si max_world est la valeur de jeton spécial `-1`, la valeur n'est pas encore connue. Elle peut continuer à être utilisée jusqu'à ce que nous rencontrions un retour en arrière qui nécessite que nous reconsidérions.

### CodeInfo

Un conteneur (généralement temporaire) pour contenir du code source abaissé.

  * `code`

    Un tableau `Any` d'instructions
  * `nomsdeslots`

    Un tableau de symboles donnant des noms pour chaque emplacement (argument ou variable locale).
  * `slotflags`

    Un tableau `UInt8` de propriétés de slot, représenté sous forme de drapeaux binaires :

      * 0x02 - assigné (seulement faux s'il n'y a *aucune* instruction d'assignation avec cette variable à gauche)
      * 0x08 - utilisé (s'il y a une lecture ou une écriture du slot)
      * 0x10 - assigné statiquement une fois
      * 0x20 - pourrait être utilisé avant d'être assigné. Ce drapeau n'est valide qu'après l'inférence de type.
  * `ssavaluetypes`

    Soit un tableau ou un `Int`.

    Si c'est un `Int`, cela donne le nombre d'emplacements temporaires insérés par le compilateur dans la fonction (la longueur du tableau `code`). Si c'est un tableau, cela spécifie un type pour chaque emplacement.
  * `ssaflags`

    Drapeaux de niveau d'instruction de 32 bits pour chaque expression dans la fonction. Voir la définition de `jl_code_info_t` dans julia.h pour plus de détails.
  * `tableau de lignes`

    Un tableau d'objets de localisation source
  * `codelocs`

    Un tableau d'indices entiers dans le `linetable`, donnant l'emplacement associé à chaque déclaration.

Champs optionnels :

  * `types de créneaux`

    Un tableau de types pour les emplacements.
  * `rettype`

    Le type de retour inféré de la forme abaissée (IR). La valeur par défaut est `Any`.
  * `méthode_pour_heuristiques_limite_inférence`

    La `method_for_inference_heuristics` étendra le générateur de la méthode donnée si nécessaire pendant l'inférence.
  * `parent`

    L'`InstanceMéthode` qui "possède" cet objet (le cas échéant).
  * `bords`

    Transférer les bords vers les instances de méthode qui doivent être invalidées.
  * `min_monde`/`max_monde`

    La plage des âges du monde pour lesquels ce code était valide au moment où il avait été inféré.

Propriétés booléennes :

  * `inféré`

    Que cela ait été produit par inférence de type.
  * `inlineable`

    Que cela devrait-il être éligible pour l'inlining.
  * `propager_entrants`

    Que cela devrait propager `@inbounds` lorsqu'il est en ligne dans le but d'éliminer les blocs `@boundscheck`.

`UInt8` paramètres :

  * `constprop`

      * 0 = utiliser une heuristique
      * 1 = agressif
      * 2 = aucun
  * `pureté` Construit à partir de 5 indicateurs de bits :

      * 0x01 << 0 = cette méthode est garantie de retourner ou de se terminer de manière cohérente (`:consistent`)
      * 0x01 << 1 = cette méthode est exempte d'effets secondaires sémantiquement visibles de l'extérieur (`:effect_free`)
      * 0x01 << 2 = cette méthode est garantie de ne pas lancer d'exception (`:nothrow`)
      * 0x01 << 3 = cette méthode est garantie de se terminer (`:terminates_globally`)
      * 0x01 << 4 = le flux de contrôle syntaxique au sein de cette méthode est garanti de se terminer (`:terminates_locally`)

    Voir la documentation de `Base.@assume_effects` pour plus de détails.
