# Custom LLVM Passes

Julia a un certain nombre de passes LLVM personnalisées. En gros, elles peuvent être classées en passes qui doivent être exécutées pour maintenir la sémantique de Julia, et des passes qui tirent parti de la sémantique de Julia pour optimiser l'IR LLVM.

## Semantic Passes

Ces passes sont utilisés pour transformer l'IR LLVM en code qui peut être exécuté sur un CPU. Leur principal objectif est de permettre à un IR plus simple d'être émis par le code générateur, ce qui permet ensuite à d'autres passes LLVM d'optimiser des motifs communs.

### CPUFeatures

  * Nom de fichier : `llvm-cpufeatures.cpp`
  * Nom de la classe : `CPUFeaturesPass`
  * Nom de l'option : `module(CPUFeatures)`

Ce passage abaisse l'intrinsèque `julia.cpu.have_fma.(f32|f64)` à vrai ou faux, en fonction de l'architecture cible et des fonctionnalités cibles présentes sur la fonction. Cet intrinsèque est souvent utilisé pour déterminer si l'utilisation d'algorithmes dépendant de l'opération rapide [fused multiply-add](https://en.wikipedia.org/wiki/Multiply%E2%80%93accumulate_operation#Fused_multiply%E2%80%93add) est préférable à l'utilisation d'algorithmes standard non dépendants de telles instructions.

### DemoteFloat16

  * Nom de fichier : `llvm-demote-float16.cpp`
  * ClassName: `DemoteFloat16Pass`
  * Nom d'option `function(DemoteFloat16)`

Ce passage remplace [float16](https://en.wikipedia.org/wiki/Half-precision_floating-point_format) opérations par des opérations float32 sur des architectures qui ne prennent pas en charge nativement les opérations float16. Cela se fait en insérant des instructions `fpext` et `fptrunc` autour de toute opération float16. Sur les architectures qui prennent en charge les opérations float16 natives, ce passage est une opération sans effet.

### LateGCLowering

  * Nom de fichier : `llvm-late-gc-lowering.cpp`
  * Nom de la classe : `LateLowerGCPass`
  * Nom de l'option : `function(LateLowerGCFrame)`

Ce passage effectue la plupart des travaux de racine GC nécessaires pour suivre les pointeurs entre les points de sauvegarde GC. Il abaisse également plusieurs intrinsics à leur traduction d'instruction correspondante, et est autorisé à violer les invariants non intégraux précédemment établis (`pointer_from_objref` est abaissé à une instruction `ptrtoint` ici). Ce passage occupe généralement le plus de temps parmi tous les passages personnalisés de Julia, en raison de son algorithme de flux de données visant à minimiser le nombre d'objets vivants à tout point de sauvegarde.

### FinalGCLowering

  * Nom de fichier : `llvm-final-gc-lowering.cpp`
  * Nom de la classe : `FinalLowerGCPass`
  * Nom de l'option : `module(FinalLowerGC)`

Ce passage réduit quelques dernières intrinsics à leur forme finale ciblant des fonctions dans la bibliothèque `libjulia`. Séparer cela de `LateGCLowering` permet à d'autres backends (compilation GPU) de fournir leurs propres réductions personnalisées pour ces intrinsics, permettant ainsi à la pipeline Julia d'être utilisée sur ces backends également.

### LowerHandlers

  * Nom de fichier : `llvm-lower-handlers.cpp`
  * Nom de la classe : `LowerExcHandlersPass`
  * Nom de l'option : `function(LowerExcHandlers)`

Ce passage réduit les intrinsics de gestion des exceptions en appels à des fonctions d'exécution qui sont réellement appelées lors de la gestion des exceptions.

### RemoveNI

  * Nom de fichier : `llvm-remove-ni.cpp`
  * Nom de la classe : `RemoveNIPass`
  * Nom de l'option : `module(RemoveNI)`

Ce passage supprime les espaces d'adresses non intégrales de la chaîne de datalayout du module. Cela permet au backend de réduire les espaces d'adresses personnalisés de Julia directement en code machine, sans une réécriture coûteuse de chaque opération de pointeur vers l'espace d'adresses 0.

### SIMDLoop

  * Nom de fichier : `llvm-simdloop.cpp`
  * Nom de la classe : `LowerSIMDLoopPass`
  * Nom de l'option : `loop(LowerSIMDLoop)`

Ce passage agit comme le principal moteur de l'annotation `@simd`. Le code généré insère un marqueur `!llvm.loopid` à l'arrière d'une boucle, que ce passage utilise pour identifier les boucles qui étaient à l'origine marquées avec `@simd`. Ensuite, ce passage recherche une chaîne d'opérations à virgule flottante qui forment une réduction et ajoute les drapeaux de mathématiques rapides `contract` et `reassoc` pour permettre la réassociation (et donc la vectorisation). Ce passage ne préserve ni les informations de boucle ni la correction de l'inférence, il peut donc violer la sémantique de Julia de manière surprenante. Si la boucle était également annotée avec `ivdep`, alors le passage marque la boucle comme n'ayant pas de dépendances portées par la boucle (le comportement résultant est indéfini si l'annotation de l'utilisateur était incorrecte ou appliquée à la mauvaise boucle).

### LowerPTLS

  * Nom de fichier : `llvm-ptls.cpp`
  * Nom de la classe : `LowerPTLSPass`
  * Nom de l'option : `module(LowerPTLSPass)`

Ce passage réduit les intrinsics Julia locaux à un thread en instructions d'assemblage. Julia s'appuie sur le stockage local au thread pour la collecte des ordures et la planification des tâches multithread. Lors de la compilation de code pour des images système et des images de paquets, ce passage remplace les appels aux intrinsics par des chargements à partir de variables globales qui sont initialisées au moment du chargement.

Si le codegen produit une fonction avec un argument et une convention d'appel `swiftself`, ce passage suppose que l'argument `swiftself` est le pgcstack et remplacera les intrinsics par cet argument. Cela permet d'accélérer les performances sur les architectures qui ont des accès lents au stockage local par thread.

### RemoveAddrspaces

  * Nom de fichier : `llvm-remove-addrspaces.cpp`
  * Nom de la classe : `RemoveAddrspacesPass`
  * Nom de l'option : `module(RemoveAddrspaces)`

Ce passage renomme les pointeurs d'un espace d'adresses à un autre espace d'adresses. Cela est utilisé pour supprimer les espaces d'adresses spécifiques à Julia du LLVM IR.

### RemoveJuliaAddrspaces

  * Nom de fichier : `llvm-remove-addrspaces.cpp`
  * Nom de la classe : `RemoveJuliaAddrspacesPass`
  * Nom de l'option : `module(RemoveJuliaAddrspaces)`

Ce passage supprime les espaces d'adresses spécifiques à Julia du LLVM IR. Il est principalement utilisé pour afficher le LLVM IR dans un format moins encombré. En interne, il est implémenté à partir du passage RemoveAddrspaces.

### Multiversioning

  * Nom de fichier : `llvm-multiversioning.cpp`
  * Nom de la classe : `MultiVersioningPass`
  * Nom de l'option : `module(JuliaMultiVersioning)`

Ce passage effectue des modifications à un module pour créer des fonctions optimisées pour s'exécuter sur différentes architectures (voir sysimg.md et pkgimg.md pour plus de détails). En termes d'implémentation, il clone des fonctions et applique différents attributs spécifiques à la cible pour permettre à l'optimiseur d'utiliser des fonctionnalités avancées telles que la vectorisation et la planification des instructions pour cette plateforme. Il crée également une infrastructure pour permettre au chargeur d'images Julia de sélectionner la version appropriée de la fonction à appeler en fonction de l'architecture sur laquelle le chargeur s'exécute. Les attributs spécifiques à la cible sont contrôlés par le drapeau de module `julia.mv.specs`, qui pendant la compilation est dérivé de la variable d'environnement [`JULIA_CPU_TARGET`](@ref JULIA_CPU_TARGET). Le passage doit également être activé en fournissant un drapeau de module `julia.mv.enable` avec une valeur de 1.

!!! warning
    L'utilisation de `llvmcall` avec le multiversioning est dangereuse. `llvmcall` permet d'accéder à des fonctionnalités généralement non exposées par les API Julia, et ne sont donc généralement pas disponibles sur toutes les architectures. Si le multiversioning est activé et qu'une génération de code est demandée pour une architecture cible qui ne prend pas en charge la fonctionnalité requise par une expression `llvmcall`, LLVM renverra probablement une erreur, probablement avec un abandon et le message `LLVM ERROR: Do not know how to split the result of this operator!`.


### GCInvariantVerifier

  * Nom de fichier : `llvm-gc-invariant-verifier.cpp`
  * Nom de la classe : `GCInvariantVerifierPass`
  * Nom de l'option : `module(GCInvariantVerifier)`

Ce passage est utilisé pour vérifier les invariants de Julia concernant l'IR LLVM. Cela inclut des éléments tels que l'inexistence de `ptrtoint` dans le [non-integral address spaces](https://llvm.org/docs/LangRef.html#non-integral-pointer-type) [^nislides] et l'existence uniquement d'instructions `addrspacecast` bénies (Suivi -> Dérivé, 0 -> Suivi, etc). Il n'effectue aucune transformation sur l'IR.

[^nislides]: https://llvm.org/devmtg/2015-02/slides/chisnall-pointers-not-int.pdf

## Optimization Passes

Ces passes sont utilisés pour effectuer des transformations sur l'IR LLVM que LLVM ne réalisera pas lui-même, par exemple la propagation des drapeaux de calcul rapide, l'analyse d'échappement et les optimisations sur des fonctions internes spécifiques à Julia. Ils utilisent des connaissances sur la sémantique de Julia pour effectuer ces optimisations.

### CombineMulAdd

  * Nom de fichier : `llvm-muladd.cpp`
  * Nom de la classe : `CombineMulAddPass`
  * Nom de l'option : `function(CombineMulAdd)`

Ce passage sert à optimiser la combinaison particulière d'un `fmul` régulier avec un `fadd` rapide en un `fmul` contracté avec un `fadd` rapide. Cela est ensuite optimisé par le backend en une instruction [fused multiply-add](https://en.wikipedia.org/wiki/Multiply%E2%80%93accumulate_operation#Fused_multiply%E2%80%93add), qui peut fournir des opérations significativement plus rapides au prix de plus de [unpredictable semantics](https://simonbyrne.github.io/notes/fastmath/).

!!! note
    Cette optimisation ne se produit que lorsque le `fmul` a une seule utilisation, qui est le `fadd` rapide.


### AllocOpt

  * Nom de fichier : `llvm-alloc-opt.cpp`
  * Nom de la classe : `AllocOptPass`
  * Nom de l'option : `function(AllocOpt)`

Julia n'a pas le concept d'une pile de programmes comme un endroit pour allouer des objets mutables. Cependant, allouer des objets sur la pile réduit la pression du GC et est essentiel pour la compilation GPU. Ainsi, `AllocOpt` effectue une conversion de la mémoire heap à la pile pour les objets qu'il peut prouver ne pas [escape](https://en.wikipedia.org/wiki/Escape_analysis) la fonction actuelle. Il effectue également un certain nombre d'autres optimisations sur les allocations, telles que la suppression des allocations qui ne sont jamais utilisées, l'optimisation des appels typeof pour les objets nouvellement alloués, et la suppression des écritures dans des allocations qui sont immédiatement écrasées. L'implémentation de l'analyse d'échappement se trouve dans `llvm-alloc-helpers.cpp`. Actuellement, ce passage n'utilise pas d'informations provenant de `EscapeAnalysis.jl`, bien que cela puisse changer à l'avenir.

### PropagateJuliaAddrspaces

  * Nom de fichier : `llvm-propagate-addrspaces.cpp`
  * Nom de la classe : `PropagateJuliaAddrspacesPass`
  * Nom de l'option : `function(PropagateJuliaAddrspaces)`

Ce passage est utilisé pour propager des espaces d'adresses spécifiques à Julia à travers des opérations sur des pointeurs. LLVM n'est pas autorisé à introduire ou à supprimer des instructions addrspacecast par des optimisations, donc ce passage agit pour éliminer les conversions addrspace redondantes en remplaçant les opérations par leur équivalent dans un espace d'adresses Julia. Pour plus d'informations sur les espaces d'adresses de Julia, voir (TODO lien vers llvm.md).

### JuliaLICM

  * Nom de fichier : `llvm-julia-licm.cpp`
  * Nom de la classe : `JuliaLICMPass`
  * Nom de l'opt : `loop(JuliaLICM)`

Ce passage est utilisé pour extraire des intrinsics spécifiques à Julia des boucles. Plus précisément, il effectue les transformations suivantes :

1. Hisser `gc_preserve_begin` et plonger `gc_preserve_end` hors des boucles lorsque les objets préservés sont invariants par rapport à la boucle.

    1. Puisque les objets préservés dans une boucle sont susceptibles d'être préservés pendant la durée de la boucle, cette transformation peut réduire le nombre de paires `gc_preserve_begin`/`gc_preserve_end` dans l'IR. Cela facilite l'identification par le `LateLowerGCPass` des endroits où des objets particuliers sont préservés.
2. Soulever les barrières d'écriture avec des objets invariants

    1. Ici, nous supposons qu'il n'y a que deux générations dont un objet peut faire partie. Étant donné cela, une barrière d'écriture n'a besoin d'être exécutée qu'une seule fois pour chaque paire du même objet. Ainsi, nous pouvons extraire les barrières d'écriture des boucles lorsque l'objet auquel on écrit est invariant par rapport à la boucle.
3. Hissez les allocations hors des boucles lorsqu'elles n'échappent pas à la boucle.

    1. Nous utilisons ici une définition très conservatrice de l'évasion, la même que celle utilisée dans `AllocOptPass`. Cette transformation peut réduire le nombre d'allocations dans l'IR, même lorsqu'une allocation échappe complètement à la fonction.

!!! note
    Ce pass est requis pour préserver l'[MemorySSA](https://llvm.org/docs/MemorySSA.html) ([Short Video](https://www.youtube.com/watch?v=bdxWmryoHak), [Longer Video](https://www.youtube.com/watch?v=1e5y6WDbXCQ)) et [ScalarEvolution](https://baziotis.cs.illinois.edu/compilers/introduction-to-scalar-evolution.html) ([Newer Slides](https://llvm.org/devmtg/2018-04/slides/Absar-ScalarEvolution.pdf) [Older Slides](https://llvm.org/devmtg/2009-10/ScalarEvolutionAndLoopOptimization.pdf)) analyses.

