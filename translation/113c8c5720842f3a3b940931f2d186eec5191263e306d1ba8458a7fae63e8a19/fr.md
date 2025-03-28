# [Package Images](@id pkgimages)

Le package Julia images fournit des caches d'objets (code natif) pour les packages Julia. Ils sont similaires à l'image système de Julia [system image](@ref dev-sysimg) et prennent en charge de nombreuses fonctionnalités similaires. En fait, le format de sérialisation sous-jacent est le même, et l'image système est l'image de base contre laquelle les images de package sont construites.

## High-level overview

Les images de package sont des bibliothèques partagées qui contiennent à la fois du code et des données. Comme les fichiers de cache `.ji`, elles sont générées par package. La section des données contient à la fois des données globales (variables globales dans le package) ainsi que les métadonnées nécessaires concernant les méthodes et types définis par le package. La section de code contient des objets natifs qui mettent en cache la sortie finale du compilateur basé sur LLVM de Julia.

L'option de ligne de commande `--pkgimages=no` peut être utilisée pour désactiver la mise en cache des objets pour cette session. Notez que cela signifie que les fichiers de cache devront probablement être régénérés. Voir [`JULIA_MAX_NUM_PRECOMPILE_FILES`](@ref JULIA_MAX_NUM_PRECOMPILE_FILES) pour la limite supérieure des variantes que Julia met en cache par défaut.

!!! note
    Bien que les images de package se présentent comme des bibliothèques partagées natives, elles ne sont qu'une approximation de celles-ci. Vous ne pourrez pas les lier à partir d'un programme natif et elles doivent être chargées depuis Julia.


## Linking

Puisque les images de package contiennent du code natif, nous devons exécuter un éditeur de liens sur elles avant de pouvoir les utiliser. Vous pouvez définir la variable d'environnement [`JULIA_VERBOSE_LINKING`](@ref JULIA_VERBOSE_LINKING) sur `true` pour rendre le processus de liaison des images de package verbeux.

De plus, nous ne pouvons pas supposer que l'utilisateur dispose d'un éditeur de liens système fonctionnel installé. Par conséquent, Julia est livrée avec LLD, l'éditeur de liens LLVM, pour offrir une expérience prête à l'emploi. Dans `base/linking.jl`, nous mettons en œuvre une interface limitée pour pouvoir lier des images de paquets sur toutes les plateformes prises en charge.

### Quirks

Malgré le fait que LLD soit un éditeur de liens multi-plateforme, il ne fournit pas une interface cohérente entre les plateformes. De plus, il est destiné à être utilisé à partir de `clang` ou d'un autre pilote de compilateur, nous réimplémentons donc une partie de la logique de `llvm-project/clang/lib/Driver/ToolChains`. Heureusement, on peut utiliser `lld -flavor` pour définir lld sur la bonne plateforme.

#### Windows

Pour éviter d'avoir à gérer `link.exe`, nous utilisons `-flavor gnu`, transformant ainsi `lld` en un lieur croisé depuis un environnement mingw32. Les DLL Windows doivent contenir une fonction `_DllMainCRTStartup` et pour minimiser notre dépendance aux bibliothèques mingw32, nous injectons nous-mêmes une définition de stub.

#### MacOS

Les bibliothèques dynamiques sur macOS doivent se lier à `-lSystem`. Sur les versions récentes de macOS, `-lSystem` n'est disponible pour la liaison que lorsque Xcode est installé. À cet effet, nous nous lions avec `-undefined dynamic_lookup`.

## [Package images optimized for multiple microarchitectures](@id pkgimgs-multi-versioning)

Semblable à [multi-versioning](@ref sysimg-multi-versioning) pour les images système, les images de package prennent en charge le multi-versioning. Si vous êtes dans un environnement hétérogène, avec un cache unifié, vous pouvez définir la variable d'environnement `JULIA_CPU_TARGET=generic` pour multi-versionner les caches d'objets.

## Flags that impact package image creation and selection

Ce sont les options de ligne de commande Julia qui impactent la sélection du cache. Les images de package qui ont été créées avec des options différentes seront rejetées.

  * `-g`, `--debug-info`: Correspondance exacte requise car cela modifie la génération de code.
  * `--check-bounds`: Correspondance exacte requise car cela modifie la génération de code.
  * `--inline`: Correspondance exacte requise car cela modifie la génération de code.
  * `--pkgimages`: Pour permettre l'exécution sans mise en cache des objets activée.
  * `-O`, `--optimize` : Rejeter les images de package générées pour un niveau d'optimisation inférieur, mais permettre le chargement de niveaux d'optimisation supérieurs.
