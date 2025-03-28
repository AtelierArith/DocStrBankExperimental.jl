# System Image Building

## [Building the Julia system image](@id Building-the-Julia-system-image)

Julia est livré avec une image système préparée contenant le contenu du module `Base`, nommée `sys.ji`. Ce fichier est également précompilé dans une bibliothèque partagée appelée `sys.{so,dll,dylib}` sur autant de plateformes que possible, afin d'offrir des temps de démarrage considérablement améliorés. Sur les systèmes qui ne sont pas livrés avec un fichier d'image système précompilé, on peut en générer un à partir des fichiers source fournis dans le dossier `DATAROOTDIR/julia/base` de Julia.

Julia générera par défaut son image système sur la moitié des threads système disponibles. Cela peut être contrôlé par la variable d'environnement [`JULIA_IMAGE_THREADS`](@ref JULIA_IMAGE_THREADS).

Cette opération est utile pour plusieurs raisons. Un utilisateur peut :

  * Construisez une image système de bibliothèque partagée précompilée sur une plateforme qui n'en était pas livrée, améliorant ainsi les temps de démarrage.
  * Modifiez `Base`, reconstruisez l'image système et utilisez le nouveau `Base` la prochaine fois que Julia est démarré.
  * Inclure un fichier `userimg.jl` qui intègre des packages dans l'image système, créant ainsi une image système qui a des packages intégrés dans l'environnement de démarrage.

Le [`PackageCompiler.jl` package](https://github.com/JuliaLang/PackageCompiler.jl) contient des fonctions d'enveloppement pratiques pour automatiser ce processus.

## [System image optimized for multiple microarchitectures](@id sysimg-multi-versioning)

L'image système peut être compilée simultanément pour plusieurs microarchitectures de CPU sous le même ensemble d'instructions (ISA). Plusieurs versions de la même fonction peuvent être créées avec un point de dispatch minimum inséré dans des fonctions partagées afin de tirer parti des différentes extensions ISA ou d'autres caractéristiques de microarchitecture. La version qui offre les meilleures performances sera sélectionnée automatiquement à l'exécution en fonction des fonctionnalités CPU disponibles.

### Specifying multiple system image targets

Une image système multi-microarchitecture peut être activée en passant plusieurs cibles lors de la compilation de l'image système. Cela peut être fait soit avec l'option make [`JULIA_CPU_TARGET`](@ref JULIA_CPU_TARGET), soit avec l'option de ligne de commande `-C` lors de l'exécution manuelle de la commande de compilation. Les cibles multiples sont séparées par `;` dans la chaîne d'options. La syntaxe pour chaque cible est un nom de CPU suivi de plusieurs fonctionnalités séparées par `,`. Toutes les fonctionnalités prises en charge par LLVM sont prises en charge et une fonctionnalité peut être désactivée avec un préfixe `-`. (Le préfixe `+` est également autorisé et ignoré pour être cohérent avec la syntaxe LLVM). De plus, quelques fonctionnalités spéciales sont prises en charge pour contrôler le comportement de clonage des fonctions.

!!! note
    Il est de bonne pratique de spécifier soit `clone_all` soit `base(<n>)` pour chaque cible à l'exception de la première. Cela rend explicite quelles cibles ont toutes les fonctions clonées, et quelles cibles sont basées sur d'autres cibles. Si cela n'est pas fait, le comportement par défaut est de ne pas cloner chaque fonction, et d'utiliser la définition de fonction de la première cible comme solution de repli lorsqu'une fonction n'est pas clonée.


1. `clone_all`

    Par défaut, seules les fonctions qui sont les plus susceptibles de bénéficier des caractéristiques de la microarchitecture seront clonées. Lorsque `clone_all` est spécifié pour une cible, cependant, **toutes** les fonctions de l'image système seront clonées pour la cible. La forme négative `-clone_all` peut être utilisée pour empêcher l'heuristique intégrée de cloner toutes les fonctions.
2. `base(<n>)`

    Où `<n>` est un espace réservé pour un nombre non négatif (par exemple, `base(0)`, `base(1)`). Par défaut, une cible partiellement clonée (c'est-à-dire pas `clone_all`) utilisera des fonctions de la cible par défaut (la première spécifiée) si une fonction n'est pas clonée. Ce comportement peut être modifié en spécifiant une base différente avec l'option `base(<n>)`. La cible `n` (indexée à partir de 0) sera utilisée comme cible de base au lieu de la cible par défaut (la `0`ème). La cible de base doit être soit `0`, soit une autre cible `clone_all`. Spécifier une cible non `clone_all` comme cible de base entraînera une erreur.
3. `opt_size`

    Cela amène la fonction cible à être optimisée pour la taille lorsqu'il n'y a pas d'impact significatif sur les performances d'exécution. Cela correspond à l'option `-Os` de GCC et Clang.
4. `min_size`

    Cela entraîne l'optimisation de la fonction pour la taille, ce qui pourrait avoir un impact significatif sur les performances à l'exécution. Cela correspond à l'option Clang `-Oz`.

En tant qu'exemple, au moment de la rédaction de ce document, la chaîne suivante est utilisée dans la création des binaires officiels `x86_64` de Julia téléchargeables sur julialang.org :

```
generic;sandybridge,-xsaveopt,clone_all;haswell,-rdrnd,base(1)
```

Cela crée une image système avec trois cibles distinctes ; une pour un processeur générique `x86_64`, une avec une architecture `sandybridge` (excluant explicitement `xsaveopt`) qui clone explicitement toutes les fonctions, et une ciblant l'architecture `haswell`, basée sur la version sysimg de `sandybridge`, et excluant également `rdrnd`. Lorsqu'une implémentation de Julia charge le sysimg généré, elle vérifiera le processeur hôte pour des indicateurs de capacité CPU correspondants, activant le niveau d'ISA le plus élevé possible. Notez que le niveau de base (`générique`) nécessite l'instruction `cx16`, qui est désactivée dans certains logiciels de virtualisation et doit être activée pour que la cible `générique` puisse être chargée. Alternativement, un sysimg pourrait être généré avec la cible `générique,-cx16` pour une plus grande compatibilité, cependant, notez que cela peut entraîner des problèmes de performance et de stabilité dans certains codes.

### Implementation overview

Ceci est un aperçu bref des différentes parties impliquées dans l'implémentation. Voir les commentaires de code pour plus de détails sur chaque composant.

1. Compilation d'image système

    La décision de parsing et de clonage est effectuée dans `src/processor*`. Nous supportons actuellement le clonage de fonctions basé sur la présence de boucles, d'instructions SIMD ou d'autres opérations mathématiques (par exemple, fastmath, fma, muladd). Cette information est transmise à `src/llvm-multiversioning.cpp` qui effectue le clonage réel. En plus de faire le clonage et d'insérer des emplacements de dispatch (voir les commentaires dans `MultiVersioning::runOnModule` pour savoir comment cela est fait), le passage génère également des métadonnées afin que le runtime puisse charger et initialiser correctement l'image système. Une description détaillée des métadonnées est disponible dans `src/processor.h`.
2. Chargement de l'image système

    Le chargement et l'initialisation de l'image système se font dans `src/processor*` en analysant les métadonnées enregistrées lors de la génération de l'image système. La détection des fonctionnalités de l'hôte et la décision de sélection sont effectuées dans `src/processor_*.cpp` en fonction de l'ISA. La sélection de la cible privilégiera une correspondance exacte du nom du CPU, une taille de registre vectoriel plus grande et un plus grand nombre de fonctionnalités. Un aperçu de ce processus se trouve dans `src/processor.cpp`.
