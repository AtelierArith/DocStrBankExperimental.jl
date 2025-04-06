# External Profiler Support

Julia offre un support explicite pour certains profileurs de traçage externes, vous permettant d'obtenir un aperçu de haut niveau du comportement d'exécution du runtime.

Les profileurs actuellement pris en charge sont :

  * [Tracy](https://github.com/wolfpld/tracy)
  * [Intel VTune (ITTAPI)](https://github.com/intel/ittapi)

### Adding New Zones

Pour ajouter de nouvelles zones, utilisez la macro `JL_TIMING`. Vous pouvez trouver de nombreux exemples dans l'ensemble du code en recherchant `JL_TIMING`. Pour ajouter un nouveau type de zone, vous l'ajoutez à `JL_TIMING_OWNERS` (et éventuellement à `JL_TIMING_EVENTS`).

### Dynamically Enabling and Disabling Zones

La variable d'environnement [`JULIA_TIMING_SUBSYSTEMS`](@ref JULIA_TIMING_SUBSYSTEMS) vous permet d'activer ou de désactiver des zones pour un exécution spécifique de Julia. Par exemple, en définissant la variable sur `+GC,-INFERENCE`, vous activerez les zones `GC` et désactiverez les zones `INFERENCE`.

## Tracy Profiler

[Tracy](https://github.com/wolfpld/tracy) est un profileur flexible qui peut être intégré de manière optionnelle avec Julia.

Une session typique de Tracy pourrait ressembler à ceci :

![Utilisation typique de Tracy](tracy.png)

### Building Julia with Tracy

Pour activer l'intégration de Tracy, construisez Julia avec l'option supplémentaire `WITH_TRACY=1` dans le fichier `Make.user`.

### Installing the Tracy Profile Viewer

La façon la plus simple d'obtenir le visualiseur de profil est d'ajouter le package `TracyProfiler_jll` et de lancer le profileur avec :

```julia
run(TracyProfiler_jll.tracy())
```

!!! note
    Sur macOS, vous voudrez peut-être définir la variable d'environnement `TRACY_DPI_SCALE` sur `1.0` si les éléments de l'interface utilisateur dans le profileur apparaissent excessivement grands.


Pour exécuter une instance "sans tête" qui enregistre la trace sur le disque, utilisez

```julia
run(`$(TracyProfiler_jll.capture()) -o mytracefile.tracy`)
```

au lieu de.

Pour des informations sur l'utilisation de l'interface utilisateur de Tracy, consultez le manuel de Tracy.

### Profiling Julia with Tracy

Un flux de travail typique pour profiler Julia avec Tracy implique de démarrer Julia en utilisant :

```julia
JULIA_WAIT_FOR_TRACY=1 ./julia -e '...'
```

La variable d'environnement garantit que Julia attend d'avoir réussi à se connecter au profileur Tracy avant de continuer l'exécution. Ensuite, utilisez l'interface utilisateur du profileur Tracy, cliquez sur `Connect`, et l'exécution de Julia devrait reprendre et le profilage devrait commencer.

### Profiling package precompilation with Tracy

Pour profiler un processus de précompilation de package, il est plus facile d'appeler explicitement `Base.compilecache` avec le package que vous souhaitez précompiler :

```julia
pkg = Base.identify_package("SparseArrays")
withenv("JULIA_WAIT_FOR_TRACY" => 1, "TRACY_PORT" => 9001) do
    Base.compilecache(pkg)
end
```

Ici, nous utilisons un port personnalisé pour Tracy, ce qui facilite la recherche du bon client dans l'interface utilisateur de Tracy pour se connecter.

### Adding metadata to zones

Les différentes fonctions `jl_timing_show_*` et `jl_timing_printf` peuvent être utilisées pour attacher une chaîne (ou des chaînes) à une zone. Par exemple, la zone de trace pour l'inférence montre l'instance de méthode qui est en cours d'inférence.

La fonction `TracyCZoneColor` peut être utilisée pour définir la couleur d'une certaine zone. Parcourez le code source pour voir comment elle est utilisée.

### Viewing Tracy files in your browser

Visitez https://topolarity.github.io/trace-viewer/ pour un visualiseur web (expérimental) pour les traces Tracy.

Vous pouvez ouvrir un fichier local `.tracy` ou fournir une URL depuis le web (par exemple, un fichier dans un dépôt Github). Si vous chargez un fichier de trace depuis le web, vous pouvez également partager l'URL de la page directement avec d'autres, leur permettant de voir la même trace.

### Enabling stack trace samples

Pour activer l'échantillonnage de la pile d'appels dans Tracy, construisez Julia avec ces options dans votre fichier `Make.user` :

```
WITH_TRACY := 1
WITH_TRACY_CALLSTACKS := 1
USE_BINARYBUILDER_LIBTRACYCLIENT := 0
```

Vous devrez peut-être également exécuter `make -C deps clean-libtracyclient` pour forcer une reconstruction de Tracy.

Cette fonctionnalité a un impact significatif sur la taille des traces et le surcoût de profilage, il est donc recommandé de désactiver l'échantillonnage de la pile d'appels lorsque cela est possible, surtout si vous avez l'intention de partager vos fichiers de trace en ligne.

Notez que le runtime JIT de Julia n'a pas encore d'intégration pour la symbolification de Tracy, donc les fonctions Julia seront généralement inconnues dans ces traces de pile.

## Intel VTune (ITTAPI) Profiler

*Cette section est encore à écrire.*
