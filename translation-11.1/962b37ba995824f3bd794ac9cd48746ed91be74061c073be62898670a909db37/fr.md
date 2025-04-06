# Fixing precompilation hangs due to open tasks or IO

Sur Julia 1.10 ou une version supérieure, vous pourriez voir le message suivant :

![Capture d'écran du blocage de précompilation](./img/precompilation_hang.png)

Cela peut se répéter. Si cela continue à se répéter sans indices que cela se résoudra de lui-même, vous pourriez avoir un "blocage de précompilation" qui nécessite une correction. Même si c'est transitoire, vous pourriez préférer le résoudre afin que les utilisateurs ne soient pas dérangés par cet avertissement. Cette page vous guide à travers l'analyse et la correction de tels problèmes.

Si vous suivez le conseil et appuyez sur `Ctrl-C`, vous pourriez voir

```
^C Interrupted: Exiting precompilation...

  1 dependency had warnings during precompilation:
┌ Test1 [ac89d554-e2ba-40bc-bc5c-de68b658c982]
│  [pid 2745] waiting for IO to finish:
│   Handle type        uv_handle_t->data
│   timer              0x55580decd1e0->0x7f94c3a4c340
```

Ce message transmet deux informations clés :

  * le blocage se produit lors de la précompilation de `Test1`, une dépendance de `Test2` (le package que nous essayions de charger avec `using Test2`)
  * pendant la précompilation de `Test1`, Julia a créé un objet `Timer` (utilisez `?Timer` si vous n'êtes pas familier avec les Timers) qui est toujours ouvert ; tant qu'il n'est pas fermé, le processus est bloqué.

Si cela vous donne suffisamment d'indice pour comprendre comment `timer = Timer(args...)` est créé, une bonne solution consiste à ajouter `wait(timer)` si `timer` se termine finalement de lui-même, ou `close(timer)` si vous devez le forcer à se fermer, avant la dernière `end` du module.

Cependant, il existe des cas qui peuvent ne pas être aussi simples. En général, la meilleure option est de commencer par déterminer si le blocage est dû au code dans Test1 ou s'il est dû à l'une des dépendances de Test1 :

  * Option 1 : `Pkg.add("Aqua")` et utilisez [`Aqua.test_persistent_tasks`](https://juliatesting.github.io/Aqua.jl/dev/#Aqua.test_persistent_tasks-Tuple{Base.PkgId}). Cela devrait vous aider à identifier quel package cause le problème, après quoi les instructions [below](@ref pchang_fix) doivent être suivies. Si nécessaire, vous pouvez créer un `PkgId` comme `Base.PkgId(UUID("..."), "Test1")`, où `...` provient de l'entrée `uuid` dans `Test1/Project.toml`.
  * Option 2 : diagnostiquer manuellement la source du blocage.

Pour diagnostiquer manuellement :

1. `Pkg.develop("Test1")`
2. Comment out all the code `include`d or defined in `Test1`, *except* the `using/import` statements.
3. Essayez à nouveau `using Test2` (ou même `using Test1` en supposant que cela bloque aussi)

Maintenant, nous arrivons à un embranchement : soit

  * le blocage persiste, indiquant qu'il s'agit de [due to one of your dependencies](@ref pchang_deps)
  * le bloc disparaît, indiquant qu'il est [due to something in your code](@ref pchang_fix).

## [Diagnosing and fixing hangs due to a package dependency](@id pchang_deps)

Utilisez une recherche binaire pour identifier la dépendance problématique : commencez par commenter la moitié de vos dépendances, puis lorsque vous isolez quelle moitié est responsable, commentez la moitié de cette moitié, etc. (Vous n'avez pas à les supprimer du projet, il suffit de commenter les déclarations `using`/`import`.)

Une fois que vous avez identifié un suspect (ici nous l'appellerons `ThePackageYouThinkIsCausingTheProblem`), essayez d'abord de précompiler ce package. S'il se bloque également lors de la précompilation, continuez à rechercher le problème en arrière.

Cependant, il est très probable que `ThePackageYouThinkIsCausingTheProblem` se précompile correctement. Cela suggère que le problème se situe dans la fonction `ThePackageYouThinkIsCausingTheProblem.__init__`, qui ne s'exécute pas lors de la précompilation de `ThePackageYouThinkIsCausingTheProblem`, mais *s'exécute* dans tout package qui charge `ThePackageYouThinkIsCausingTheProblem`. Pour tester cette théorie, mettez en place un exemple de travail minimal (MWE), quelque chose comme

```julia
(@v1.10) pkg> generate MWE
  Generating  project MWE:
    MWE\Project.toml
    MWE\src\MWE.jl
```

où se trouve le code source de `MWE.jl`

```julia
module MWE
using ThePackageYouThinkIsCausingTheProblem
end
```

et vous avez ajouté `ThePackageYouThinkIsCausingTheProblem` aux dépendances de MWE.

Si ce MWE reproduit le blocage, vous avez trouvé votre coupable : `ThePackageYouThinkIsCausingTheProblem.__init__` doit créer l'objet `Timer`. Si l'objet timer peut être fermé en toute sécurité, c'est une bonne option. Sinon, la solution la plus courante consiste à éviter de créer le timer pendant que *n'importe quel* package est en cours de précompilation : ajoutez

```julia
ccall(:jl_generating_output, Cint, ()) == 1 && return nothing
```

en tant que première ligne de `ThePackageYouThinkIsCausingTheProblem.__init__`, et cela évitera toute initialisation dans tout processus Julia dont le but est de précompiler des packages.

## [Fixing package code to avoid hangs](@id pchang_fix)

Recherchez dans votre package des mots suggestifs (ici comme "Timer") et voyez si vous pouvez identifier où le problème est créé. Notez qu'une *définition* de méthode comme

```julia
maketimer() = Timer(timer -> println("hi"), 0; interval=1)
```

n'est pas problématique en soi : cela peut causer ce problème uniquement si `maketimer` est appelé pendant que le module est en cours de définition. Cela pourrait se produire à partir d'une instruction de niveau supérieur telle que

```julia
const GLOBAL_TIMER = maketimer()
```

ou cela pourrait éventuellement se produire dans un [precompile workload](https://github.com/JuliaLang/PrecompileTools.jl).

Si vous avez du mal à identifier les lignes causales, envisagez de faire une recherche binaire : commentez des sections de votre package (ou `incluez` des lignes pour omettre des fichiers entiers) jusqu'à ce que vous ayez réduit le problème en portée.
