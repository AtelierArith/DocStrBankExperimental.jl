# `EscapeAnalysis`

`Core.Compiler.EscapeAnalysis` est un module utilitaire du compilateur qui vise à analyser les informations d'évasion de [Julia's SSA-form IR](@ref Julia-SSA-form-IR), également connu sous le nom de `IRCode`.

Cette analyse d'évasion vise à :

  * tirer parti de la sémantique de haut niveau de Julia, en particulier raisonner sur les échappements et l'aliasing via des appels inter-procédures
  * soyez suffisamment polyvalent pour être utilisé pour diverses optimisations, y compris [alias-aware SROA](https://github.com/JuliaLang/julia/pull/43888), [early `finalize` insertion](https://github.com/JuliaLang/julia/pull/44056), [copy-free `ImmutableArray` construction](https://github.com/JuliaLang/julia/pull/42465), allocation de pile d'objets mutables, et ainsi de suite.
  * réaliser une implémentation simple basée sur une analyse de flux de données entièrement rétrograde ainsi qu'un nouveau design de treillis qui combine des propriétés de treillis orthogonales

## Try it out!

Vous pouvez essayer l'analyse d'évasion en chargeant le script utilitaire `EAUtils.jl` qui définit les entrées de commodité `code_escapes` et `@code_escapes` à des fins de test et de débogage :

```@repl EAUtils
let JULIA_DIR = normpath(Sys.BINDIR, "..", "share", "julia")
    # load `EscapeAnalysis` module to define the core analysis code
    include(normpath(JULIA_DIR, "base", "compiler", "ssair", "EscapeAnalysis", "EscapeAnalysis.jl"))
    using .EscapeAnalysis
    # load `EAUtils` module to define the utilities
    include(normpath(JULIA_DIR, "test", "compiler", "EscapeAnalysis", "EAUtils.jl"))
    using .EAUtils
end

mutable struct SafeRef{T}
    x::T
end
Base.getindex(x::SafeRef) = x.x;
Base.setindex!(x::SafeRef, v) = x.x = v;
Base.isassigned(x::SafeRef) = true;
get′(x) = isassigned(x) ? x[] : throw(x);

result = code_escapes((String,String,String,String)) do s1, s2, s3, s4
    r1 = Ref(s1)
    r2 = Ref(s2)
    r3 = SafeRef(s3)
    try
        s1 = get′(r1)
        ret = sizeof(s1)
    catch err
        global GV = err # will definitely escape `r1`
    end
    s2 = get′(r2)       # still `r2` doesn't escape fully
    s3 = get′(r3)       # still `r3` doesn't escape fully
    s4 = sizeof(s4)     # the argument `s4` doesn't escape here
    return s2, s3, s4
end
```

Les symboles sur le côté de chaque argument d'appel et des déclarations SSA représentent la signification suivante :

  * `◌` (plain) : cette valeur n'est pas analysée car les informations d'échappement ne seront de toute façon pas utilisées (lorsque l'objet est `isbitstype` par exemple)
  * `✓` (vert ou cyan) : cette valeur ne s'échappe jamais (`has_no_escape(result.state[x])` est vrai), coloré en bleu si elle a également une échappée d'argument (`has_arg_escape(result.state[x])` est vrai)
  * `↑` (bleu ou jaune) : cette valeur peut s'échapper vers l'appelant via le retour (`has_return_escape(result.state[x])` est vrai), coloré en jaune si elle a également une échappée lancée non gérée (`has_thrown_escape(result.state[x])` est vrai)
  * `X` (rouge) : cette valeur peut s'échapper vers un endroit que l'analyse d'évasion ne peut pas raisonner, comme des évasions vers une mémoire globale (`has_all_escape(result.state[x])` est vrai)
  * `*` (gras) : l'état d'échappement de cette valeur se situe entre le `ReturnEscape` et le `AllEscape` dans l'ordre partiel de [`EscapeInfo`](@ref Core.Compiler.EscapeAnalysis.EscapeInfo), coloré en jaune s'il a un échappement lancé non géré également (`has_thrown_escape(result.state[x])` est vrai)
  * `′`: cette valeur a des informations supplémentaires sur le champ d'objet / l'élément de tableau dans sa propriété `AliasInfo`

Les informations d'échappement de chaque argument d'appel et de chaque valeur SSA peuvent être inspectées de manière programmatique comme suit :

```@repl EAUtils
result.state[Core.Argument(3)] # get EscapeInfo of `s2`

result.state[Core.SSAValue(3)] # get EscapeInfo of `r3`
```

## Analysis Design

### Lattice Design

`EscapeAnalysis` est implémenté comme un [data-flow analysis](https://en.wikipedia.org/wiki/Data-flow_analysis) qui fonctionne sur un réseau de [`x::EscapeInfo`](@ref Core.Compiler.EscapeAnalysis.EscapeInfo), qui est composé des propriétés suivantes :

  * `x.Analyzed::Bool` : pas formellement partie de la structure de treillis, indique seulement que `x` n'a pas été analysé ou non.
  * `x.ReturnEscape::BitSet`: enregistre les instructions SSA où `x` peut s'échapper vers l'appelant via le retour
  * `x.ThrownEscape::BitSet` : enregistre les instructions SSA où `x` peut être lancé comme exception (utilisé pour le [exception handling](@ref EA-Exception-Handling) décrit ci-dessous)
  * `x.AliasInfo`: maintains all possible values that can be aliased to fields or array elements of `x` (used for the [alias analysis](@ref EA-Alias-Analysis) described below)
  * `x.ArgEscape::Int` (pas encore implémenté) : indique qu'il s'échappera vers l'appelant via `setfield!` sur l'argument(s)

Ces attributs peuvent être combinés pour créer un treillis partiel qui a une hauteur finie, étant donné l'invariant qu'un programme d'entrée a un nombre fini d'instructions, ce qui est assuré par la sémantique de Julia. La partie astucieuse de ce design de treillis est qu'elle permet une mise en œuvre plus simple des opérations de treillis en leur permettant de gérer chaque propriété de treillis séparément[^LatticeDesign].

### Backward Escape Propagation

Cette implémentation de l'analyse d'échappement est basée sur l'algorithme de flux de données décrit dans l'article[^MM02]. L'analyse fonctionne sur la structure de `EscapeInfo` et fait passer les éléments de la structure du bas vers le haut jusqu'à ce que chaque élément de la structure converge vers un point fixe en maintenant un ensemble de travail (conceptuel) qui contient des compteurs de programme correspondant aux instructions SSA restantes à analyser. L'analyse gère un état global unique qui suit `EscapeInfo` de chaque argument et instruction SSA, mais note également qu'une certaine sensibilité au flux est codée sous forme de compteurs de programme enregistrés dans la propriété `ReturnEscape` de `EscapeInfo`, qui peuvent être combinés avec l'analyse de domination par la suite pour raisonner sur la sensibilité au flux si nécessaire.

Un design distinctif de cette analyse d'évasion est qu'elle est entièrement *rétrograde*, c'est-à-dire que les informations d'évasion circulent *des utilisations vers les définitions*. Par exemple, dans l'extrait de code ci-dessous, l'AE analyse d'abord l'instruction `return %1` et impose `ReturnEscape` sur `%1` (correspondant à `obj`), puis elle analyse `%1 = %new(Base.RefValue{String, _2}))` et propage le `ReturnEscape` imposé sur `%1` à l'argument d'appel `_2` (correspondant à `s`) :

```@repl EAUtils
code_escapes((String,)) do s
    obj = Ref(s)
    return obj
end
```

L'observation clé ici est que cette analyse rétrograde permet à l'information d'évasion de circuler naturellement le long de la chaîne d'utilisation-définition plutôt que le flux de contrôle[^BackandForth]. En conséquence, ce schéma permet une mise en œuvre simple de l'analyse d'évasion, par exemple, `PhiNode` peut être géré simplement en propageant l'information d'évasion imposée sur un `PhiNode` à ses valeurs prédécesseurs :

```@repl EAUtils
code_escapes((Bool, String, String)) do cnd, s, t
    if cnd
        obj = Ref(s)
    else
        obj = Ref(t)
    end
    return obj
end
```

### [Alias Analysis](@id EA-Alias-Analysis)

`EscapeAnalysis` implémente une analyse de champ en arrière pour raisonner sur les échappements imposés aux champs d'objet avec une certaine précision, et la propriété `x.AliasInfo` de `x::EscapeInfo` existe à cette fin. Elle enregistre toutes les valeurs possibles qui peuvent être aliasées aux champs de `x` aux sites de "utilisation", puis les informations d'échappement de ces valeurs enregistrées sont propagées aux valeurs de champ réelles plus tard aux sites de "définition". Plus précisément, l'analyse enregistre une valeur qui peut être aliasée à un champ d'objet en analysant l'appel `getfield`, puis elle propage ses informations d'échappement au champ lors de l'analyse de l'expression `%new(...)` ou de l'appel `setfield!`[^Dynamism].

```@repl EAUtils
code_escapes((String,)) do s
    obj = SafeRef("init")
    obj[] = s
    v = obj[]
    return v
end
```

Dans l'exemple ci-dessus, `ReturnEscape` imposé sur `%3` (correspondant à `v`) n'est *pas* directement propagé à `%1` (correspondant à `obj`), mais plutôt que `ReturnEscape` est seulement propagé à `_2` (correspondant à `s`). Ici, `%3` est enregistré dans la propriété `AliasInfo` de `%1` car il peut être aliasé au premier champ de `%1`, et ensuite, lors de l'analyse de `Base.setfield!(%1, :x, _2)::String`, cette information d'évasion est propagée à `_2` mais pas à `%1`.

Donc `EscapeAnalysis` suit quels éléments IR peuvent être aliasés à travers une chaîne `getfield`-`%new`/`setfield!` afin d'analyser les échappements des champs d'objet, mais en réalité, cette analyse d'alias doit être généralisée pour gérer d'autres éléments IR également. Cela est dû au fait qu'en IR Julia, le même objet est parfois représenté par différents éléments IR et nous devons donc nous assurer que ces différents éléments IR qui peuvent en réalité représenter le même objet partagent les mêmes informations d'échappement. Les éléments IR qui retournent le même objet que leur(s) opérande(s), tels que `PiNode` et `typeassert`, peuvent provoquer cet aliasing au niveau IR et nécessitent donc que les informations d'échappement imposées à l'un de ces valeurs aliasées soient partagées entre elles. Plus intéressant encore, cela est également nécessaire pour raisonner correctement sur les mutations sur `PhiNode`. Considérons l'exemple suivant :

```@repl EAUtils
code_escapes((Bool, String,)) do cond, x
    if cond
        ϕ2 = ϕ1 = SafeRef("foo")
    else
        ϕ2 = ϕ1 = SafeRef("bar")
    end
    ϕ2[] = x
    y = ϕ1[]
    return y
end
```

`ϕ1 = %5` et `ϕ2 = %6` sont aliasés et donc `ReturnEscape` imposé sur `%8 = Base.getfield(%6, :x)::String` (correspondant à `y = ϕ1[]`) doit être propagé à `Base.setfield!(%5, :x, _3)::String` (correspondant à `ϕ2[] = x`). Afin que ces informations d'évasion soient propagées correctement, l'analyse doit reconnaître que les *prédécesseurs* de `ϕ1` et `ϕ2` peuvent également être aliasés et égaliser leurs informations d'évasion.

Une propriété intéressante de ces informations d'aliasing est qu'elles ne sont pas connues au site de "utilisation" mais ne peuvent être dérivées qu'au site de "définition" (car l'aliasing est conceptuellement équivalent à une affectation), et donc cela ne s'intègre pas naturellement dans une analyse rétrograde. Afin de propager efficacement les informations d'évasion entre des valeurs liées, EscapeAnalysis.jl utilise une approche inspirée de l'algorithme d'analyse d'évasion expliqué dans un ancien article de la JVM[^JVM05]. C'est-à-dire qu'en plus de gérer les éléments de la lattique d'évasion, l'analyse maintient également un ensemble d'alias "équi", un ensemble disjoint d'arguments et d'instructions SSA aliasés. L'ensemble d'alias gère les valeurs qui peuvent être aliasées les unes aux autres et permet d'égaliser les informations d'évasion imposées à l'une de ces valeurs aliasées entre elles.

### [Array Analysis](@id EA-Array-Analysis)

L'analyse des alias pour les champs d'objet décrite ci-dessus peut également être généralisée pour analyser les opérations sur les tableaux. `EscapeAnalysis` implémente des gestions pour diverses opérations de tableau primitives afin qu'il puisse propager les échappements via la chaîne d'utilisation-définition `arrayref`-`arrayset` et ne pas échapper aux tableaux alloués de manière trop conservatrice :

```@repl EAUtils
code_escapes((String,)) do s
    ary = Any[]
    push!(ary, SafeRef(s))
    return ary[1], length(ary)
end
```

Dans l'exemple ci-dessus, `EscapeAnalysis` comprend que `%20` et `%2` (correspondant à l'objet alloué `SafeRef(s)`) sont aliasés via la chaîne `arrayset`-`arrayref` et impose `ReturnEscape` sur eux, mais ne l'impose pas sur le tableau alloué `%1` (correspondant à `ary`). `EscapeAnalysis` impose toujours `ThrownEscape` sur `ary` car il doit également tenir compte des échappements potentiels via `BoundsError`, mais notez également que de tels `ThrownEscape` non gérés peuvent souvent être ignorés lors de l'optimisation de l'allocation de `ary`.

De plus, dans les cas où les informations sur les indices de tableau ainsi que les dimensions du tableau peuvent être connues *précisément*, `EscapeAnalysis` est capable de raisonner même sur l'aliasing "par élément" via la chaîne `arrayref`-`arrayset`, tout comme `EscapeAnalysis` effectue une analyse d'alias "par champ" pour les objets :

```@repl EAUtils
code_escapes((String,String)) do s, t
    ary = Vector{Any}(undef, 2)
    ary[1] = SafeRef(s)
    ary[2] = SafeRef(t)
    return ary[1], length(ary)
end
```

Notez que `ReturnEscape` n'est imposé que sur `%2` (correspondant à `SafeRef(s)`) mais pas sur `%4` (correspondant à `SafeRef(t)`). Cela est dû au fait que la dimension du tableau alloué et les indices impliqués dans toutes les opérations `arrayref`/`arrayset` sont disponibles en tant qu'informations constantes et que `EscapeAnalysis` peut comprendre que `%6` est aliasé à `%2` mais ne peut jamais être aliasé à `%4`. Dans ce genre de cas, les passes d'optimisation suivantes seront capables de remplacer `Base.arrayref(true, %1, 1)::Any` par `%2` (également connu sous le nom de "load-forwarding") et finalement d'éliminer complètement l'allocation du tableau `%1` (également connu sous le nom de "scalar-replacement").

Lorsqu'on compare l'analyse des champs d'objet, où un accès à un champ d'objet peut être analysé de manière triviale en utilisant des informations de type dérivées par inférence, la dimension des tableaux n'est pas encodée comme information de type et nous avons donc besoin d'une analyse supplémentaire pour en dériver cette information. `EscapeAnalysis` à ce moment effectue d'abord un simple scan linéaire supplémentaire pour analyser les dimensions des tableaux alloués avant de lancer la routine principale d'analyse afin que l'analyse d'échappement suivante puisse analyser précisément les opérations sur ces tableaux.

Cependant, une telle analyse d'alias "par élément" précise est souvent difficile. Essentiellement, la principale difficulté inhérente aux tableaux est que la dimension et l'index du tableau sont souvent non constants :

  * la boucle produit souvent des indices de tableau non constants et variant de boucle
  * (specific to vectors) le redimensionnement d'un tableau change la dimension du tableau et invalide sa constance.

Discutons de ces difficultés avec des exemples concrets.

Dans l'exemple suivant, `EscapeAnalysis` échoue l'analyse d'alias précise puisque l'index à `Base.arrayset(false, %4, %8, %6)::Vector{Any}` n'est pas (triviellement) constant. En particulier, `Any[nothing, nothing]` forme une boucle et appelle cette opération `arrayset` dans une boucle, où `%6` est représenté comme une valeur de nœud ϕ (dont la valeur dépend du flux de contrôle). En conséquence, `ReturnEscape` se retrouve imposé à la fois sur `%23` (correspondant à `SafeRef(s)`) et `%25` (correspondant à `SafeRef(t)`), bien qu'idéalement nous souhaitions qu'il soit imposé uniquement sur `%23` mais pas sur `%25` :

```@repl EAUtils
code_escapes((String,String)) do s, t
    ary = Any[nothing, nothing]
    ary[1] = SafeRef(s)
    ary[2] = SafeRef(t)
    return ary[1], length(ary)
end
```

L'exemple suivant illustre comment le redimensionnement des vecteurs rend l'analyse des alias précise difficile. La difficulté essentielle est que la dimension du tableau alloué `%1` est d'abord initialisée à `0`, mais elle change par les deux appels `:jl_array_grow_end` par la suite. `EscapeAnalysis` abandonne actuellement simplement l'analyse des alias précise chaque fois qu'il rencontre des opérations de redimensionnement de tableau et donc `ReturnEscape` est imposé à la fois sur `%2` (correspondant à `SafeRef(s)`) et `%20` (correspondant à `SafeRef(t)`):

```@repl EAUtils
code_escapes((String,String)) do s, t
    ary = Any[]
    push!(ary, SafeRef(s))
    push!(ary, SafeRef(t))
    ary[1], length(ary)
end
```

Pour résoudre ces difficultés, nous devons faire en sorte que l'inférence prenne en compte les dimensions des tableaux et propage les dimensions des tableaux de manière sensible au flux[^ArrayDimension], ainsi que proposer une belle représentation des valeurs variant en boucle.

`EscapeAnalysis` à ce moment passe rapidement à l'analyse plus imprécise qui ne suit pas les informations d'index précises dans les cas où les dimensions du tableau ou les indices ne sont trivialement pas constants. Le changement peut naturellement être implémenté comme une opération de jointure de treillis de la propriété `EscapeInfo.AliasInfo` dans le cadre d'analyse de flux de données.

### [Exception Handling](@id EA-Exception-Handling)

Il convient également de noter comment `EscapeAnalysis` gère les éventuelles échappées via des exceptions. Naïvement, il semble suffisant de propager les informations d'échappement imposées sur l'objet `:the_exception` à toutes les valeurs qui peuvent être lancées dans un bloc `try` correspondant. Mais il existe en réalité plusieurs autres façons d'accéder à l'objet d'exception dans Julia, telles que `Base.current_exceptions` et `rethrow`. Par exemple, l'analyse d'échappement doit tenir compte de l'échappement potentiel de `r` dans l'exemple ci-dessous :

```@repl EAUtils
const GR = Ref{Any}();
@noinline function rethrow_escape!()
    try
        rethrow()
    catch err
        GR[] = err
    end
end;
get′(x) = isassigned(x) ? x[] : throw(x);

code_escapes() do
    r = Ref{String}()
    local t
    try
        t = get′(r)
    catch err
        t = typeof(err)   # `err` (which `r` aliases to) doesn't escape here
        rethrow_escape!() # but `r` escapes here
    end
    return t
end
```

Cela nécessite une analyse globale afin de raisonner correctement sur toutes les échappatoires possibles via les interfaces d'exception existantes. Pour l'instant, nous propagons toujours les informations d'échappatoire les plus élevées à tous les objets potentiellement lancés de manière conservatrice, car une telle analyse supplémentaire pourrait ne pas valoir la peine d'être effectuée étant donné que la gestion des exceptions et les chemins d'erreur n'ont généralement pas besoin d'être très sensibles à la performance, et que les optimisations des chemins d'erreur pourraient de toute façon être très inefficaces, car elles sont souvent même "non optimisées" intentionnellement pour des raisons de latence.

`x::EscapeInfo`'s `x.ThrownEscape` propriété enregistre les instructions SSA où `x` peut être lancé en tant qu'exception. En utilisant cette information, `EscapeAnalysis` peut propager les échappements possibles via des exceptions de manière limitée uniquement à ceux qui peuvent être lancés dans chaque région `try` :

```@repl EAUtils
result = code_escapes((String,String)) do s1, s2
    r1 = Ref(s1)
    r2 = Ref(s2)
    local ret
    try
        s1 = get′(r1)
        ret = sizeof(s1)
    catch err
        global GV = err # will definitely escape `r1`
    end
    s2 = get′(r2)       # still `r2` doesn't escape fully
    return s2
end
```

## Analysis Usage

`analyze_escapes` est le point d'entrée pour analyser les informations d'évasion des éléments SSA-IR.

La plupart des optimisations comme SROA (`sroa_pass!`) sont plus efficaces lorsqu'elles sont appliquées à une source optimisée que le passage d'inlining (`ssa_inlining_pass!`) a simplifiée en résolvant les appels inter-procédures et en développant les sources des fonctions appelées. En conséquence, `analyze_escapes` est également capable d'analyser l'IR post-inlining et de collecter des informations sur les échappements qui sont utiles pour certaines optimisations liées à la mémoire.

Cependant, comme certaines passes d'optimisation comme l'inlining peuvent modifier les flux de contrôle et éliminer le code mort, elles peuvent rompre la validité inter-procédurale des informations d'échappement. En particulier, pour collecter des informations d'échappement valides inter-procéduralement, nous devons analyser un IR pré-inlining.

Pour cette raison, `analyze_escapes` peut analyser `IRCode` à n'importe quel stade d'optimisation au niveau de Julia, et en particulier, il est censé être utilisé aux deux étapes suivantes :

  * `IPO EA` : analyser l'IR pré-inlining pour générer un cache d'informations d'échappement valide pour l'IPO
  * `Local EA` : analyser l'IR post-inlining pour collecter des informations d'échappement valides localement.

Les informations d'évasion dérivées par `IPO EA` sont transformées en la structure de données `ArgEscapeCache` et mises en cache globalement. En passant un rappel approprié `get_escape_cache` à `analyze_escapes`, l'analyse des évasions peut améliorer la précision de l'analyse en utilisant les informations inter-procédurales mises en cache des appelés non inlinés qui ont été dérivées par le précédent `IPO EA`. Plus intéressant encore, il est également valide d'utiliser les informations d'évasion `IPO EA` pour l'inférence de type, par exemple, la précision de l'inférence peut être améliorée en formant `Const`/`PartialStruct`/`MustAlias` d'un objet mutable.

```@docs
Core.Compiler.EscapeAnalysis.analyze_escapes
Core.Compiler.EscapeAnalysis.EscapeState
Core.Compiler.EscapeAnalysis.EscapeInfo
```

---

[^LatticeDesign]: Our type inference implementation takes the alternative approach, where each lattice property is represented by a special lattice element type object. It turns out that it started to complicate implementations of the lattice operations mainly because it often requires conversion rules between each lattice element type object. And we are working on [overhauling our type inference lattice implementation](https://github.com/JuliaLang/julia/pull/42596) with `EscapeInfo`-like lattice design.

[^MM02]: *A Graph-Free approach to Data-Flow Analysis*.      Markas Mohnen, 2002, April.      [https://api.semanticscholar.org/CorpusID:28519618](https://api.semanticscholar.org/CorpusID:28519618).

[^BackandForth]: Our type inference algorithm in contrast is implemented as a forward analysis, because type information usually flows from "definition" to "usage" and it is more natural and effective to propagate such information in a forward way.

[^Dynamism]: In some cases, however, object fields can't be analyzed precisely. For example, object may escape to somewhere `EscapeAnalysis` can't account for possible memory effects on it, or fields of the objects simply can't be known because of the lack of type information. In such cases `AliasInfo` property is raised to the topmost element within its own lattice order, and it causes succeeding field analysis to be conservative and escape information imposed on fields of an unanalyzable object to be propagated to the object itself.

[^JVM05]: *Escape Analysis in the Context of Dynamic Compilation and Deoptimization*.       Thomas Kotzmann and Hanspeter Mössenböck, 2005, June.       [https://dl.acm.org/doi/10.1145/1064979.1064996](https://dl.acm.org/doi/10.1145/1064979.1064996).

[^ArrayDimension]: Otherwise we will need yet another forward data-flow analysis on top of the escape analysis.
