# Eval of Julia code

L'une des parties les plus difficiles de l'apprentissage de la façon dont le langage Julia exécute du code est d'apprendre comment toutes les pièces fonctionnent ensemble pour exécuter un bloc de code.

Chaque morceau de code passe généralement par de nombreuses étapes avec des noms potentiellement inconnus, tels que (dans aucun ordre particulier) : flisp, AST, C++, LLVM, `eval`, `typeinf`, `macroexpand`, sysimg (ou image système), bootstrap, compiler, analyser, exécuter, JIT, interpréter, box, unbox, fonction intrinsèque et fonction primitive, avant de se transformer en résultat souhaité (espérons-le).

!!! sidebar "Definitions"
      * REPL

        REPL signifie Read-Eval-Print Loop. C'est juste ce que nous appelons l'environnement de ligne de commande pour faire court.
      * AST

        Arbre de syntaxe abstraite L'AST est la représentation numérique de la structure du code. Sous cette forme, le code a été tokenisé pour en extraire le sens afin qu'il soit plus adapté à la manipulation et à l'exécution.


![Diagramme du flux du compilateur](./img/compiler_diagram.png)

## Julia Execution

La vue d'ensemble à 10 000 pieds de l'ensemble du processus est la suivante :

1. L'utilisateur démarre `julia`.
2. La fonction C `main()` de `cli/loader_exe.c` est appelée. Cette fonction traite les arguments de la ligne de commande, remplissant la structure `jl_options` et définissant la variable `ARGS`. Elle initialise ensuite Julia (en appelant [`julia_init` in `init.c`](https://github.com/JuliaLang/julia/blob/master/src/init.c), ce qui peut charger un [sysimg](@ref dev-sysimg) précédemment compilé. Enfin, elle passe le contrôle à Julia en appelant [`Base._start()`](https://github.com/JuliaLang/julia/blob/master/base/client.jl).
3. Lorsque `_start()` prend le contrôle, la séquence suivante de commandes dépend des arguments de ligne de commande fournis. Par exemple, si un nom de fichier a été fourni, il procédera à l'exécution de ce fichier. Sinon, il commencera un REPL interactif.
4. En sautant les détails sur la façon dont le REPL interagit avec l'utilisateur, disons simplement que le programme se retrouve avec un bloc de code qu'il souhaite exécuter.
5. Si le bloc de code à exécuter se trouve dans un fichier, [`jl_load(char *filename)`](https://github.com/JuliaLang/julia/blob/master/src/toplevel.c) est invoqué pour charger le fichier et [parse](@ref dev-parsing) le. Chaque fragment de code est ensuite passé à `eval` pour être exécuté.
6. Chaque fragment de code (ou AST) est transmis à [`eval()`](@ref) pour être transformé en résultats.
7. [`eval()`](@ref) prend chaque fragment de code et essaie de l'exécuter dans [`jl_toplevel_eval_flex()`](https://github.com/JuliaLang/julia/blob/master/src/toplevel.c).
8. `jl_toplevel_eval_flex()` décide si le code est une action "toplevel" (comme `using` ou `module`), ce qui serait invalide à l'intérieur d'une fonction. Si c'est le cas, il transmet le code à l'interpréteur de niveau supérieur.
9. `jl_toplevel_eval_flex()` puis [expands](@ref dev-macro-expansion) le code pour éliminer toutes les macros et pour "abaisser" l'AST afin de le rendre plus simple à exécuter.
10. `jl_toplevel_eval_flex()` utilise ensuite quelques heuristiques simples pour décider s'il doit compiler à la volée l'AST ou l'interpréter directement.
11. La majeure partie du travail d'interprétation du code est gérée par [`eval` in `interpreter.c`](https://github.com/JuliaLang/julia/blob/master/src/interpreter.c).
12. Si au lieu de cela, le code est compilé, la majeure partie du travail est gérée par `codegen.cpp`. Chaque fois qu'une fonction Julia est appelée pour la première fois avec un ensemble donné de types d'arguments, [type inference](@ref dev-type-inference) sera exécuté sur cette fonction. Ces informations sont utilisées par l'étape [codegen](@ref dev-codegen) pour générer un code plus rapide.
13. Finalement, l'utilisateur quitte le REPL, ou la fin du programme est atteinte, et la méthode `_start()` retourne.
14. Juste avant de sortir, `main()` appelle [`jl_atexit_hook(exit_code)`](https://github.com/JuliaLang/julia/blob/master/src/init.c). Cela appelle `Base._atexit()` (qui appelle toutes les fonctions enregistrées à [`atexit()`](@ref) à l'intérieur de Julia). Ensuite, il appelle [`jl_gc_run_all_finalizers()`](https://github.com/JuliaLang/julia/blob/master/src/gc.c). Enfin, il nettoie gracieusement tous les handles `libuv` et attend qu'ils se vident et se ferment.

## [Parsing](@id dev-parsing)

Le parseur Julia est un petit programme lisp écrit en femtolisp, dont le code source est distribué à l'intérieur de Julia dans [src/flisp](https://github.com/JuliaLang/julia/tree/master/src/flisp).

L'interface des fonctions pour cela est principalement définie dans [`jlfrontend.scm`](https://github.com/JuliaLang/julia/blob/master/src/jlfrontend.scm). Le code dans [`ast.c`](https://github.com/JuliaLang/julia/blob/master/src/ast.c) gère ce transfert du côté de Julia.

Les autres fichiers pertinents à ce stade sont [`julia-parser.scm`](https://github.com/JuliaLang/julia/blob/master/src/julia-parser.scm), qui gère la tokenisation du code Julia et le transforme en un AST, et [`julia-syntax.scm`](https://github.com/JuliaLang/julia/blob/master/src/julia-syntax.scm), qui gère la transformation des représentations AST complexes en représentations AST plus simples, "abaissées", qui sont plus adaptées à l'analyse et à l'exécution.

Si vous souhaitez tester le parseur sans reconstruire entièrement Julia, vous pouvez exécuter le frontend de manière autonome comme suit :

```
$ cd src
$ flisp/flisp
> (load "jlfrontend.scm")
> (jl-parse-file "<filename>")
```

## [Macro Expansion](@id dev-macro-expansion)

Lorsque [`eval()`](@ref) rencontre un macro, il développe ce nœud AST avant d'essayer d'évaluer l'expression. L'expansion de macro implique un transfert de `4d61726b646f776e2e436f64652822222c20226576616c28292229_40726566` (en Julia), à la fonction de parsing `jl_macroexpand()` (écrite en `flisp`) au macro Julia lui-même (écrit en - quoi d'autre - Julia) via `fl_invoke_julia_macro()`, et retour.

Typiquement, l'expansion de macro est invoquée comme première étape lors d'un appel à [`Meta.lower()`](@ref)/`jl_expand()`, bien qu'elle puisse également être invoquée directement par un appel à [`macroexpand()`](@ref)/`jl_macroexpand()`.

## [Type Inference](@id dev-type-inference)

L'inférence de type est implémentée en Julia par [`typeinf()` in `compiler/typeinfer.jl`](https://github.com/JuliaLang/julia/blob/master/base/compiler/typeinfer.jl). L'inférence de type est le processus d'examen d'une fonction Julia et de détermination des limites pour les types de chacune de ses variables, ainsi que des limites sur le type de la valeur de retour de la fonction. Cela permet de nombreuses optimisations futures, telles que le déboxing de valeurs immuables connues et le levage à la compilation de diverses opérations d'exécution telles que le calcul des décalages de champ et des pointeurs de fonction. L'inférence de type peut également inclure d'autres étapes telles que la propagation de constantes et l'inlining.

!!! sidebar "More Definitions"
      * JIT

        Just-In-Time Compilation Le processus de génération de code machine natif en mémoire au moment où il est nécessaire.
      * LLVM

        Machine Virtuelle de Bas Niveau (un compilateur) Le compilateur JIT de Julia est un programme/bibliothèque appelé libLLVM. La génération de code dans Julia fait référence à la fois au processus de prise d'un AST Julia et de le transformer en instructions LLVM, et au processus d'optimisation de LLVM qui le transforme en instructions d'assemblage natives.
      * C++

        Le langage de programmation dans lequel LLVM est implémenté, ce qui signifie que le codegen est également implémenté dans ce langage. Le reste de la bibliothèque de Julia est implémenté en C, en partie parce que son ensemble de fonctionnalités plus réduit le rend plus utilisable en tant que couche d'interface entre les langages.
      * boîte

        Ce terme est utilisé pour décrire le processus de prise d'une valeur et d'allocation d'un wrapper autour des données qui sont suivies par le ramasse-miettes (gc) et qui sont étiquetées avec le type de l'objet.
      * déballer

        L'inverse de l'encapsulation d'une valeur. Cette opération permet une manipulation plus efficace des données lorsque le type de ces données est entièrement connu au moment de la compilation (grâce à l'inférence de type).
      * fonction générique

        Une fonction Julia composée de plusieurs "méthodes" qui sont sélectionnées pour le dispatch dynamique en fonction de la signature de type des arguments.
      * fonction anonyme ou "méthode"

        Une fonction Julia sans nom et sans capacités de dispatch de type
      * fonction primitive

        Une fonction implémentée en C mais exposée en Julia comme une fonction nommée "méthode" (bien que sans capacités de dispatch de fonction générique, similaire à une fonction anonyme)
      * fonction intrinsèque

        Une opération de bas niveau exposée sous forme de fonction en Julia. Ces pseudo-fonctions implémentent des opérations sur des bits bruts telles que l'addition et l'extension de signe qui ne peuvent pas être exprimées directement de toute autre manière. Comme elles opèrent directement sur les bits, elles doivent être compilées en une fonction et entourées d'un appel à `Core.Intrinsics.box(T, ...)` pour réaffecter des informations de type à la valeur.


## [JIT Code Generation](@id dev-codegen)

Codegen est le processus de transformation d'un AST Julia en code machine natif.

L'environnement JIT est initialisé par un appel précoce à [`jl_init_codegen` in `codegen.cpp`](https://github.com/JuliaLang/julia/blob/master/src/codegen.cpp).

À la demande, une méthode Julia est convertie en une fonction native par la fonction `emit_function(jl_method_instance_t*)`. (notez que lors de l'utilisation du MCJIT (dans LLVM v3.4+), chaque fonction doit être JIT dans un nouveau module.) Cette fonction appelle récursivement `emit_expr()` jusqu'à ce que l'ensemble de la fonction ait été émis.

Une grande partie du reste de ce fichier est consacrée à diverses optimisations manuelles de modèles de code spécifiques. Par exemple, `emit_known_call()` sait comment intégrer de nombreuses fonctions primitives (définies dans [`builtins.c`](https://github.com/JuliaLang/julia/blob/master/src/builtins.c)) pour diverses combinaisons de types d'arguments.

D'autres parties de codegen sont gérées par divers fichiers d'aide :

  * [`debuginfo.cpp`](https://github.com/JuliaLang/julia/blob/master/src/debuginfo.cpp)

    Gère les traces de retour pour les fonctions JIT
  * [`ccall.cpp`](https://github.com/JuliaLang/julia/blob/master/src/ccall.cpp)

    Gère le ccall et llvmcall FFI, ainsi que divers fichiers `abi_*.cpp`
  * [`intrinsics.cpp`](https://github.com/JuliaLang/julia/blob/master/src/intrinsics.cpp)

    Gère l'émission de diverses fonctions intrinsèques de bas niveau

!!! sidebar "Bootstrapping"
    Le processus de création d'une nouvelle image système s'appelle "bootstrapping".

    L'étymologie de ce mot vient de l'expression "se tirer soi-même par les bottes", et fait référence à l'idée de commencer à partir d'un ensemble très limité de fonctions et de définitions disponibles et de finir par la création d'un environnement complet.


## [System Image](@id dev-sysimg)

L'image système est une archive précompilée d'un ensemble de fichiers Julia. Le fichier `sys.ji` distribué avec Julia est l'une de ces images système, générée en exécutant le fichier [`sysimg.jl`](https://github.com/JuliaLang/julia/blob/master/base/sysimg.jl), et en sérialisant l'environnement résultant (y compris les Types, Fonctions, Modules, et toutes les autres valeurs définies) dans un fichier. Par conséquent, il contient une version figée des modules `Main`, `Core`, et `Base` (et tout ce qui était dans l'environnement à la fin du démarrage). Ce sérialiseur/désérialiseur est implémenté par [`jl_save_system_image`/`jl_restore_system_image` in `staticdata.c`](https://github.com/JuliaLang/julia/blob/master/src/staticdata.c).

Si aucun fichier sysimg n'existe (`jl_options.image_file == NULL`), cela implique également que `--build` a été donné en ligne de commande, donc le résultat final devrait être un nouveau fichier sysimg. Lors de l'initialisation de Julia, des modules `Core` et `Main` minimaux sont créés. Ensuite, un fichier nommé `boot.jl` est évalué à partir du répertoire courant. Julia évalue ensuite tout fichier donné comme argument de ligne de commande jusqu'à ce qu'elle atteigne la fin. Enfin, elle enregistre l'environnement résultant dans un fichier "sysimg" pour être utilisé comme point de départ pour une future exécution de Julia.
