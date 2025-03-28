# Building Julia (Detailed)

## Downloading the Julia source code

Si vous êtes derrière un pare-feu, vous devrez peut-être utiliser le protocole `https` au lieu du protocole `git` :

```sh
git config --global url."https://".insteadOf git://
```

Assurez-vous également de configurer votre système pour utiliser les paramètres de proxy appropriés, par exemple en définissant les variables `https_proxy` et `http_proxy`.

## Building Julia

Lors de la première compilation, le build téléchargera automatiquement le pré-construit [external dependencies](#Required-Build-Tools-and-External-Libraries). Si vous préférez construire toutes les dépendances vous-même, ou si vous construisez sur un système qui ne peut pas accéder au réseau pendant le processus de construction, ajoutez ce qui suit dans `Make.user` :

```
USE_BINARYBUILDER=0
```

La construction de Julia nécessite 5 Go si toutes les dépendances sont construites et environ 4 Go de mémoire virtuelle.

Pour effectuer une construction parallèle, utilisez `make -j N` et fournissez le nombre maximum de processus concurrents. Si les valeurs par défaut dans la construction ne fonctionnent pas pour vous, et que vous devez définir des paramètres make spécifiques, vous pouvez les enregistrer dans `Make.user`, et placer le fichier à la racine de votre source Julia. La construction vérifiera automatiquement l'existence de `Make.user` et l'utilisera si elle existe.

Vous pouvez créer des builds hors-arbre de Julia en spécifiant `make O=<répertoire-de-build> configure` dans la ligne de commande. Cela créera un miroir de répertoire, avec tous les Makefiles nécessaires pour construire Julia, dans le répertoire spécifié. Ces builds partageront les fichiers sources dans Julia et `deps/srccache`. Chaque répertoire de build hors-arbre peut avoir son propre fichier `Make.user` pour remplacer le fichier global `Make.user` dans le dossier de niveau supérieur.

Si tout fonctionne correctement, vous verrez une bannière Julia et un invite interactive dans laquelle vous pouvez entrer des expressions pour évaluation. (Les erreurs liées aux bibliothèques peuvent être causées par de vieilles bibliothèques incompatibles présentes dans votre PATH. Dans ce cas, essayez de déplacer le répertoire `julia` plus tôt dans le PATH). Notez que la plupart des instructions ci-dessus s'appliquent aux systèmes unix.

Pour exécuter Julia de n'importe où, vous pouvez :

  * ajoutez un alias (dans `bash` : `echo "alias julia='/path/to/install/folder/bin/julia'" >> ~/.bashrc && source ~/.bashrc`), ou
  * ajoutez un lien symbolique vers l'exécutable `julia` dans le répertoire `julia` vers `/usr/local/bin` (ou tout autre répertoire approprié déjà dans votre chemin), ou
  * ajoutez le répertoire `julia` à votre chemin exécutable pour cette session de shell (dans `bash` : `export PATH="$(pwd):$PATH"` ; dans `csh` ou `tcsh` :

`set path= ( $path $cwd )` ), ou

  * ajoutez le répertoire `julia` à votre chemin exécutable de manière permanente (par exemple, dans `.bash_profile`), ou
  * écrivez `prefix=/path/to/install/folder` dans `Make.user` puis exécutez `make install`. S'il y a une version de Julia déjà installée dans ce dossier, vous devez la supprimer avant d'exécuter `make install`.

Certaines des options que vous pouvez définir pour contrôler la construction de Julia sont énumérées et documentées au début du fichier `Make.inc`, mais vous ne devez jamais l'éditer à cette fin, utilisez plutôt `Make.user`.

Les Makefiles de Julia définissent des règles automatiques pratiques appelées `print-<VARNAME>` pour imprimer la valeur des variables, en remplaçant `<VARNAME>` par le nom de la variable dont on souhaite imprimer la valeur. Par exemple

```console
$ make print-JULIA_PRECOMPILE
JULIA_PRECOMPILE=1
```

Ces règles sont utiles à des fins de débogage.

Maintenant, vous devriez être en mesure d'exécuter Julia comme ceci :

```
julia
```

Si vous construisez un package Julia pour distribution sur Linux, macOS ou Windows, jetez un œil aux notes détaillées dans [distributing.md](https://github.com/JuliaLang/julia/blob/master/doc/src/devdocs/build/distributing.md).

## Updating an existing source tree

Si vous avez précédemment téléchargé `julia` en utilisant `git clone`, vous pouvez mettre à jour l'arborescence source existante en utilisant `git pull` plutôt qu'en recommençant à zéro :

```sh
cd julia
git pull && make
```

En supposant que vous n'ayez apporté aucune modification à l'arborescence source qui entrerait en conflit avec les mises à jour en amont, ces commandes déclencheront une construction pour se mettre à jour vers la dernière version.

## General troubleshooting

1. Au fil du temps, la bibliothèque de base peut accumuler suffisamment de changements pour que le processus de démarrage lors de la création de l'image système échoue. Si cela se produit, la construction peut échouer avec une erreur comme

    ```sh
     *** This error is usually fixed by running 'make clean'. If the error persists, try 'make cleanall' ***
    ```

    Comme décrit, exécuter `make clean && make` est généralement suffisant. Parfois, un nettoyage plus approfondi effectué par `make cleanall` est nécessaire.
2. De nouvelles versions de dépendances externes peuvent être introduites, ce qui peut parfois provoquer des conflits avec les versions antérieures des builds existants.

    a. Des cibles `make` spéciales existent pour aider à effacer la construction existante d'une dépendance. Par exemple, `make -C deps clean-llvm` nettoiera la construction existante de `llvm` afin que `llvm` soit reconstruit à partir de la distribution source téléchargée la prochaine fois que `make` est appelé. `make -C deps distclean-llvm` est un nettoyage plus fort qui supprimera également la distribution source téléchargée, garantissant qu'une nouvelle copie de la distribution source sera téléchargée et que tout nouveau correctif sera appliqué la prochaine fois que `make` est appelé.

    b. Pour supprimer les binaires existants de `julia` et toutes ses dépendances, supprimez le répertoire `./usr` *dans l'arborescence source*.
3. Si vous avez récemment mis à jour macOS, assurez-vous d'exécuter `xcode-select --install` pour mettre à jour les outils en ligne de commande. Sinon, vous pourriez rencontrer des erreurs liées à des en-têtes et des bibliothèques manquants, comme `ld: library not found for -lcrt1.10.6.o`.
4. Si vous avez déplacé le répertoire source, vous pourriez rencontrer des erreurs telles que `CMake Error: The current CMakeCache.txt directory ... is different than the directory ... where CMakeCache.txt was created.`, auquel cas vous pouvez supprimer la dépendance problématique sous `deps`.
5. Dans des cas extrêmes, vous souhaiterez peut-être réinitialiser l'arbre source à un état vierge. Les commandes git suivantes peuvent être utiles :

    ```sh
     git reset --hard #Forcibly remove any changes to any files under version control
     git clean -x -f -d #Forcibly remove any file or directory not under version control
    ```

    *Pour éviter de perdre du travail, assurez-vous de savoir ce que ces commandes font avant de les exécuter. `git` ne pourra pas annuler ces modifications !*

## Platform-Specific Notes

Notes pour divers systèmes d'exploitation :

  * [Linux](https://github.com/JuliaLang/julia/blob/master/doc/src/devdocs/build/linux.md)
  * [macOS](https://github.com/JuliaLang/julia/blob/master/doc/src/devdocs/build/macos.md)
  * [Windows](https://github.com/JuliaLang/julia/blob/master/doc/src/devdocs/build/windows.md)
  * [FreeBSD](https://github.com/JuliaLang/julia/blob/master/doc/src/devdocs/build/freebsd.md)

Notes pour diverses architectures :

  * [ARM](https://github.com/JuliaLang/julia/blob/master/doc/src/devdocs/build/arm.md)

## Required Build Tools and External Libraries

La construction de Julia nécessite que le logiciel suivant soit installé :

  * **[GNU make]**                — construction des dépendances.
  * **[gcc & g++][gcc]** (>= 7.1) ou **[Clang][clang]** (>= 5.0, >= 9.3 pour Apple Clang) — compilation et liaison de C, C++.
  * **[libatomic][gcc]**          — fourni par **[gcc]** et nécessaire pour prendre en charge les opérations atomiques.
  * **[python]** (>=2.7)          — nécessaire pour construire LLVM.
  * **[gfortran]**                — compilation et liaison des bibliothèques Fortran.
  * **[perl]**                    — prétraitement des fichiers d'en-tête des bibliothèques.
  * **[wget]**, **[curl]**, ou **[fetch]** (FreeBSD) — pour télécharger automatiquement des bibliothèques externes.
  * **[m4]**                      — nécessaire pour construire GMP.
  * **[awk]**                     — outil d'aide pour les Makefiles.
  * **[patch]**                   — pour modifier le code source.
  * **[cmake]** (>= 3.4.3)        — nécessaire pour construire `libgit2`.
  * **[pkg-config]**              — nécessaire pour construire `libgit2` correctement, en particulier pour le support des proxies.
  * **[powershell]** (>= 3.0)     — nécessaire uniquement sur Windows.
  * **[qui]**                   — nécessaire pour vérifier les dépendances de construction.

Sur les distributions basées sur Debian (par exemple, Ubuntu), vous pouvez les installer facilement avec `apt-get` :

```
sudo apt-get install build-essential libatomic1 python gfortran perl wget m4 cmake pkg-config curl
```

Julia utilise les bibliothèques externes suivantes, qui sont automatiquement téléchargées (ou dans quelques cas, incluses dans le dépôt source de Julia) et ensuite compilées à partir du code source la première fois que vous exécutez `make`. Les numéros de version spécifiques de ces bibliothèques que Julia utilise sont listés dans [`deps/$(libname).version`](https://github.com/JuliaLang/julia/blob/master/deps/).

  * **[LLVM]** (15.0 + [patches](https://github.com/JuliaLang/llvm-project/tree/julia-release/15.x)) — infrastructure de compilation (voir [note below](#llvm)).
  * **[FemtoLisp]**            — emballé avec le code source de Julia, et utilisé pour implémenter l'interface du compilateur.
  * **[libuv]**  (fork personnalisé) — bibliothèque d'E/S basée sur des événements, portable et haute performance.
  * **[OpenLibm]**             — bibliothèque libm portable contenant des fonctions mathématiques élémentaires.
  * **[DSFMT]**                — bibliothèque de générateur de nombres pseudorandom Mersenne Twister rapide.
  * **[OpenBLAS]**             — rapide, ouvert et maintenu [sous-programmes de base d'algèbre linéaire (BLAS)]
  * **[LAPACK]**               — bibliothèque de routines d'algèbre linéaire pour résoudre des systèmes d'équations linéaires simultanées, des solutions des moindres carrés de systèmes d'équations linéaires, des problèmes de valeurs propres et des problèmes de valeurs singulières.
  * **[MKL]** (optionnel)       – OpenBLAS et LAPACK peuvent être remplacés par la bibliothèque MKL d'Intel.
  * **[SuiteSparse]**          — bibliothèque de routines d'algèbre linéaire pour matrices creuses.
  * **[PCRE]**                 — Bibliothèque d'expressions régulières compatibles avec Perl.
  * **[GMP]**                  — Bibliothèque d'arithmétique à précision multiple GNU, nécessaire pour le support de `BigInt`.
  * **[MPFR]**                 — Bibliothèque GNU de flottants à précision multiple, nécessaire pour le support des flottants à précision arbitraire (`BigFloat`).
  * **[libgit2]**              — Bibliothèque Git liée, utilisée par le gestionnaire de paquets de Julia.
  * **[curl]**                 — libcurl fournit un support de téléchargement et de proxy.
  * **[libssh2]**              — bibliothèque pour le transport SSH, utilisée par libgit2 pour les paquets avec des télécommandes SSH.
  * **[mbedtls]**              — bibliothèque utilisée pour la cryptographie et la sécurité de la couche de transport, utilisée par libssh2
  * **[utf8proc]**             — une bibliothèque pour le traitement des chaînes Unicode encodées en UTF-8.
  * **[LLVM libunwind]**       — La version d'LLVM de [libunwind], une bibliothèque qui détermine la chaîne d'appels d'un programme.
  * **[ITTAPI]**               — Technologie d'instrumentation et de traçage d'Intel et API Just-In-Time.

[GNU make]:     https://www.gnu.org/software/make [patch]:        https://www.gnu.org/software/patch [wget]:         https://www.gnu.org/software/wget [m4]:           https://www.gnu.org/software/m4 [awk]:          https://www.gnu.org/software/gawk [gcc]:          https://gcc.gnu.org [clang]:        https://clang.llvm.org [python]:       https://www.python.org/ [gfortran]:     https://gcc.gnu.org/fortran/ [curl]:         https://curl.haxx.se [fetch]:        https://www.freebsd.org/cgi/man.cgi?fetch(1) [perl]:         https://www.perl.org [cmake]:        https://www.cmake.org [OpenLibm]:     https://github.com/JuliaLang/openlibm [DSFMT]:        https://github.com/MersenneTwister-Lab/dSFMT [OpenBLAS]:     https://github.com/xianyi/OpenBLAS [LAPACK]:       https://www.netlib.org/lapack [MKL]:          https://software.intel.com/en-us/articles/intel-mkl [SuiteSparse]:  https://people.engr.tamu.edu/davis/suitesparse.html [PCRE]:         https://www.pcre.org [LLVM]:         https://www.llvm.org [LLVM libunwind]: https://github.com/llvm/llvm-project/tree/main/libunwind [FemtoLisp]:    https://github.com/JeffBezanson/femtolisp [GMP]:          https://gmplib.org [MPFR]:         https://www.mpfr.org [libuv]:        https://github.com/JuliaLang/libuv [libgit2]:      https://libgit2.org/ [utf8proc]:     https://julialang.org/utf8proc/ [libunwind]:    https://www.nongnu.org/libunwind [libssh2]:      https://www.libssh2.org [mbedtls]:      https://tls.mbed.org/ [pkg-config]:   https://www.freedesktop.org/wiki/Software/pkg-config/ [powershell]:   https://docs.microsoft.com/en-us/powershell/scripting/wmf/overview [which]:        https://carlowood.github.io/which/ [ITTAPI]:       https://github.com/intel/ittapi

## Build dependencies

Si vous avez déjà un ou plusieurs de ces packages installés sur votre système, vous pouvez empêcher Julia de compiler des duplicatas de ces bibliothèques en passant `USE_SYSTEM_...=1` à `make` ou en ajoutant la ligne à `Make.user`. La liste complète des drapeaux possibles peut être trouvée dans `Make.inc`.

Veuillez noter que cette procédure n'est pas officiellement supportée, car elle introduit une variabilité supplémentaire dans l'installation et la version des dépendances, et est recommandée uniquement pour les mainteneurs de paquets système. Des erreurs de compilation inattendues peuvent survenir, car le système de construction ne fera aucun contrôle supplémentaire pour s'assurer que les paquets appropriés sont installés.

### LLVM

La dépendance la plus compliquée est LLVM, pour laquelle nous nécessitons des correctifs supplémentaires de la part de l'amont (LLVM n'est pas compatible avec les versions antérieures).

Pour emballer Julia avec LLVM, nous recommandons soit :

  * regrouper une bibliothèque LLVM uniquement Julia à l'intérieur du package Julia, ou
  * ajouter les correctifs au package LLVM de la distribution.

      * Une liste complète des correctifs est disponible sur [Github](https://github.com/JuliaLang/llvm-project), voir la branche `julia-release/15.x`.
      * Le seul correctif spécifique à Julia est le renommage de la bibliothèque (`llvm7-symver-jlprefix.patch`), qui ne doit *pas* être appliqué à un LLVM système.
      * Les correctifs restants sont tous des corrections de bogues en amont et ont été contribué à LLVM en amont.

L'utilisation d'une version non corrigée ou différente d'LLVM entraînera des erreurs et/ou de mauvaises performances. Vous pouvez construire une version différente d'LLVM à partir d'un dépôt Git distant avec les options suivantes dans le fichier `Make.user` :

```make
# Force source build of LLVM
USE_BINARYBUILDER_LLVM = 0
# Use Git for fetching LLVM source code
# this is either `1` to get all of them
DEPS_GIT = 1
# or a space-separated list of specific dependencies to download with git
DEPS_GIT = llvm

# Other useful options:
#URL of the Git repository you want to obtain LLVM from:
#  LLVM_GIT_URL = ...
#Name of the alternate branch to clone from git
#  LLVM_BRANCH = julia-16.0.6-0
#SHA hash of the alterate commit to check out automatically
#  LLVM_SHA1 = $(LLVM_BRANCH)
#List of LLVM targets to build.  It is strongly recommended to keep at least all the
#default targets listed in `deps/llvm.mk`, even if you don't necessarily need all of them.
#  LLVM_TARGETS = ...
#Use ccache for faster recompilation in case you need to restart a build.
#  USECCACHE = 1
#  CMAKE_GENERATOR=Ninja
#  LLVM_ASSERTIONS=1
#  LLVM_DEBUG=Symbols
```

Les différentes phases de construction sont contrôlées par des fichiers spécifiques :

  * `deps/llvm.version` : touchez ou modifiez pour vérifier une nouvelle version, `make get-llvm check-llvm`
  * `deps/srccache/llvm/source-extracted` : résultat de `make extract-llvm`
  * `deps/llvm/build_Release*/build-configured` : résultat de `make configure-llvm`
  * `deps/llvm/build_Release*/build-configured` : résultat de `make compile-llvm`
  * `usr-staging/llvm/build_Release*.tgz` : résultat de `make stage-llvm` (régénérer avec `make reinstall-llvm`)
  * `usr/manifest/llvm` : résultat de `make install-llvm` (régénérer avec `make uninstall-llvm`)
  * `make version-check-llvm` : s'exécute à chaque fois pour avertir l'utilisateur s'il y a des modifications locales.

Bien que Julia puisse être construite avec des versions plus récentes d'LLVM, le support de cela doit être considéré comme expérimental et non adapté à l'emballage.

### libuv

Julia utilise un fork personnalisé de libuv. C'est une petite dépendance, et peut être intégrée en toute sécurité dans le même package que Julia, sans entrer en conflit avec la bibliothèque système. Les builds de Julia ne devraient *pas* essayer d'utiliser la libuv système.

### BLAS and LAPACK

En tant que langage numérique haute performance, Julia devrait être lié à un BLAS et LAPACK multi-threadés, tels qu'OpenBLAS ou ATLAS, qui offriront des performances bien meilleures que les implémentations de référence `libblas` qui peuvent être par défaut sur certains systèmes.

## Source distributions of releases

Chaque pré-version et version de Julia a une distribution source "complète" et une distribution source "légère".

La distribution source complète contient le code source de Julia et toutes les dépendances afin qu'il puisse être construit à partir du code source sans connexion Internet. La distribution source légère n'inclut pas le code source des dépendances.

Par exemple, `julia-1.0.0.tar.gz` est la distribution de code source léger pour la version `v1.0.0` de Julia, tandis que `julia-1.0.0-full.tar.gz` est la distribution de code source complète.

## Building Julia from source with a Git checkout of a stdlib

Si vous devez compiler Julia à partir des sources avec un checkout Git d'une stdlib, utilisez `make DEPS_GIT=NAME_OF_STDLIB` lors de la compilation de Julia.

Par exemple, si vous devez compiler Julia à partir des sources avec un checkout Git de Pkg, utilisez `make DEPS_GIT=Pkg` lors de la compilation de Julia. Le dépôt `Pkg` se trouve dans `stdlib/Pkg`, et a été créé initialement avec un `HEAD` détaché. Si vous faites cela à partir d'un dépôt Julia existant, vous devrez peut-être exécuter `make clean` au préalable.

Si vous devez construire Julia à partir des sources avec des vérifications Git de plus d'une bibliothèque standard, alors `DEPS_GIT` doit être une liste séparée par des espaces des noms des bibliothèques standard. Par exemple, si vous devez construire Julia à partir des sources avec une vérification Git de Pkg, Tar et Downloads, utilisez `make DEPS_GIT='Pkg Tar Downloads'` lors de la construction de Julia.

## Building an "assert build" of Julia

Un "build d'assertion" de Julia est un build qui a été construit avec à la fois `FORCE_ASSERTIONS=1` et `LLVM_ASSERTIONS=1`. Pour construire un build d'assertion, définissez les deux variables suivantes dans votre fichier `Make.user` :

```
FORCE_ASSERTIONS=1
LLVM_ASSERTIONS=1
```

Veuillez noter que les versions assert de Julia seront plus lentes que les versions régulières (non-assert).

## Building 32-bit Julia on a 64-bit machine

Occasionnellement, des bogues spécifiques aux architectures 32 bits peuvent survenir, et lorsque cela se produit, il est utile de pouvoir déboguer le problème sur votre machine locale. Étant donné que la plupart des systèmes modernes 64 bits prennent en charge l'exécution de programmes construits pour des systèmes 32 bits, si vous n'avez pas besoin de recompiler Julia à partir de la source (par exemple, si vous devez principalement inspecter le comportement d'une version 32 bits de Julia sans toucher au code C), vous pouvez probablement utiliser une version 32 bits de Julia pour votre système que vous pouvez obtenir à partir de [official downloads page](https://julialang.org/downloads/). Cependant, si vous devez recompiler Julia à partir de la source, une option consiste à utiliser un conteneur Docker d'un système 32 bits. Du moins pour l'instant, construire une version 32 bits de Julia est relativement simple en utilisant [ubuntu 32-bit docker images](https://hub.docker.com/r/i386/ubuntu). En bref, après avoir configuré `docker`, voici les étapes requises :

```sh
$ docker pull i386/ubuntu
$ docker run --platform i386 -i -t i386/ubuntu /bin/bash
```

À ce stade, vous devriez être dans une console de machine 32 bits (notez que `uname` rapporte l'architecture de l'hôte, donc indiquera toujours 64 bits, mais cela n'affectera pas la construction de Julia). Vous pouvez ajouter des packages et compiler du code ; lorsque vous `exit`, tous les changements seront perdus, alors assurez-vous de terminer votre analyse en une seule session ou de mettre en place un script que vous pouvez copier/coller pour configurer votre environnement.

À partir de ce point, vous devriez

```sh
# apt update
```

(Notez que `sudo` n'est pas installé, mais il n'est pas nécessaire non plus puisque vous êtes connecté en tant que `root`, donc vous pouvez omettre `sudo` de toutes les commandes.)

Ensuite, ajoutez tous les [build dependencies](#required-build-tools-and-external-libraries), un éditeur basé sur la console de votre choix, `git`, et tout ce dont vous aurez besoin (par exemple, `gdb`, `rr`, etc.). Choisissez un répertoire dans lequel travailler et `git clone` Julia, vérifiez la branche que vous souhaitez déboguer et construisez Julia comme d'habitude.

## Update the version number of a dependency

Il existe deux types de constructions.

1. Construire tout (`deps/` et `src/`) à partir du code source.  (Ajoutez `USE_BINARYBUILDER=0` à `Make.user`, voir [Building Julia](#building-julia))
2. Construire à partir de la source (`src/`) avec des dépendances précompilées (par défaut)

Lorsque vous souhaitez mettre à jour le numéro de version d'une dépendance dans `deps/`, vous voudrez peut-être utiliser la liste de contrôle suivante :

```md
### Check list

Version numbers:
- [ ] `deps/$(libname).version`: `LIBNAME_VER`, `LIBNAME_BRANCH`, `LIBNAME_SHA1` and `LIBNAME_JLL_VER`
- [ ] `stdlib/$(LIBNAME_JLL_NAME)_jll/Project.toml`: `version`

Checksum:
- [ ] `deps/checksums/$(libname)`
- [ ] `deps/checksums/$(LIBNAME_JLL_NAME)-*/`: `md5` and `sha512`

Patches:
- [ ] `deps/$(libname).mk`
- [ ] `deps/patches/$(libname)-*.patch`
```

Remarque :

  * Pour des dépendances spécifiques, certains éléments de la liste de contrôle peuvent ne pas exister.
  * Pour le fichier de somme de contrôle, il peut s'agir **d'un seul fichier** sans suffixe, ou **d'un dossier** contenant deux fichiers.

### Example: `OpenLibm`

1. Mettre à jour les numéros de version dans `deps/openlibm.version`

      * `OPENLIBM_VER := 0.X.Y`
      * `OPENLIBM_BRANCH = v0.X.Y`
      * `OPENLIBM_SHA1 = nouvelle-hachage-sha1`
2. Mettre à jour le numéro de version dans `stdlib/OpenLibm_jll/Project.toml`

      * `version = "0.X.Y+0"`
3. Mettre à jour les sommes de contrôle dans `deps/checksums/openlibm`

      * `make -f contrib/refresh_checksums.mk openlibm`
4. Vérifiez si les fichiers de correctif `deps/patches/openlibm-*.patch` existent.

      * si les correctifs n'existent pas, passez.
      * si des correctifs existent, vérifiez s'ils ont été fusionnés dans la nouvelle version et doivent être supprimés. Lors de la suppression d'un correctif, n'oubliez pas de modifier le fichier Makefile correspondant (`deps/openlibm.mk`).
