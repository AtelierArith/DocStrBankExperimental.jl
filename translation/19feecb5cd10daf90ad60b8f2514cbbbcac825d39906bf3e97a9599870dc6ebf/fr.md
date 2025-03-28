# Sanitizer support

[Sanitizers](https://github.com/google/sanitizers) peut être utilisé dans des constructions personnalisées de Julia pour faciliter la détection de certains types d'erreurs dans le code interne C/C++ de Julia.

## Address Sanitizer: easy build

À partir d'un checkout source de Julia, vous devriez être en mesure de construire une version prenant en charge la sanitisation d'adresse dans Julia et LLVM comme suit :

```sh
$ mkdir /tmp/julia
$ contrib/asan/build.sh /tmp/julia/
```

Ici, nous avons choisi `/tmp/julia` comme répertoire de construction, mais vous pouvez choisir ce que vous souhaitez. Une fois construit, exécutez la charge de travail que vous souhaitez tester avec `/tmp/julia/julia`. Les bugs de mémoire entraîneront des erreurs.

Si vous avez besoin de personnalisation ou de plus de détails, consultez la documentation ci-dessous.

## General considerations

Utiliser les sanitizers de Clang nécessite évidemment d'utiliser Clang (`USECLANG=1`), mais il y a un autre piège : la plupart des sanitizers nécessitent une bibliothèque d'exécution, fournie par le compilateur hôte, tandis que le code instrumenté généré par le JIT de Julia s'appuie sur des fonctionnalités de cette bibliothèque. Cela implique que la version LLVM de votre compilateur hôte doit correspondre à celle de la bibliothèque LLVM utilisée dans Julia.

Une solution facile consiste à avoir un dossier de construction dédié pour fournir un outil de correspondance, en construisant avec `BUILD_LLVM_CLANG=1`. Vous pouvez ensuite vous référer à cet outil à partir d'un autre dossier de construction en spécifiant `USECLANG=1` tout en remplaçant les variables `CC` et `CXX`.

Les erreurs des sanitizers se produisent lorsqu'ils détectent qu'une bibliothèque partagée est ouverte en utilisant `RTLD_DEEPBIND` (réf : [google/sanitizers#611](https://github.com/google/sanitizers/issues/611)). Étant donné que [libblastrampoline](https://github.com/staticfloat/libblastrampoline) utilise par défaut `RTLD_DEEPBIND`, nous devons définir la variable d'environnement `LBT_USE_RTLD_DEEPBIND=0` lors de l'utilisation d'un sanitizer.

Pour utiliser l'un des assainisseurs, définissez `SANITIZE=1` puis le drapeau approprié pour l'assainisseur que vous souhaitez utiliser.

Sur macOS, cela pourrait nécessiter des drapeaux supplémentaires pour fonctionner. Dans l'ensemble, cela pourrait ressembler à ceci, plus un ou plusieurs des drapeaux `SANITIZE_*` énumérés ci-dessous :

```
make -C deps USE_BINARYBUILDER_LLVM=0 LLVM_VER=svn stage-llvm

make -C src SANITIZE=1 USECLANG=1 \
    CC=~+/deps/scratch/llvm-svn/build_Release/bin/clang \
    CXX=~+/deps/scratch/llvm-svn/build_Release/bin/clang++ \
    CPPFLAGS="-isysroot $(xcode-select -p)/Platforms/MacOSX.platform/Developer/SDKs/MacOSX.sdk" \
    CXXFLAGS="-isystem $(xcode-select -p)/Toolchains/XcodeDefault.xctoolchain/usr/include/c++/v1"
```

(ou mettez-les dans votre `Make.user`, afin de ne pas avoir à les retenir à chaque fois).

## Address Sanitizer (ASAN)

Pour détecter ou déboguer des bugs de mémoire, vous pouvez utiliser [address sanitizer (ASAN)](https://clang.llvm.org/docs/AddressSanitizer.html) de Clang. En compilant avec `SANITIZE_ADDRESS=1`, vous activez ASAN pour le compilateur Julia et son code généré. De plus, vous pouvez spécifier `LLVM_SANITIZE=1` pour assainir la bibliothèque LLVM également. Notez que ces options entraînent un coût élevé en performance et en mémoire. Par exemple, l'utilisation d'ASAN pour Julia et LLVM fait que `testall1` prend 8 à 10 fois plus de temps tout en utilisant 20 fois plus de mémoire (cela peut être réduit respectivement à un facteur de 3 et 4 en utilisant les options décrites ci-dessous).

Par défaut, Julia définit le drapeau ASAN `allow_user_segv_handler=1`, qui est nécessaire pour que la livraison des signaux fonctionne correctement. Vous pouvez définir d'autres options en utilisant le drapeau d'environnement `ASAN_OPTIONS`, auquel cas vous devrez répéter l'option par défaut mentionnée précédemment. Par exemple, l'utilisation de la mémoire peut être réduite en spécifiant `fast_unwind_on_malloc=0` et `malloc_context_size=2`, au prix de l'exactitude de la trace de pile. Pour l'instant, Julia définit également `detect_leaks=0`, mais cela devrait être supprimé à l'avenir.

### Example setup

#### Step 1: Install toolchain

Vérifiez un worktree Git (ou créez un répertoire de construction hors arbre) à `$TOOLCHAIN_WORKTREE` et créez un fichier de configuration `$TOOLCHAIN_WORKTREE/Make.user` avec

```
USE_BINARYBUILDER_LLVM=1
BUILD_LLVM_CLANG=1
```

Exécuter :

```sh
cd $TOOLCHAIN_WORKTREE
make -C deps install-llvm install-clang install-llvm-tools
```

pour installer les binaires de l'outil dans `$TOOLCHAIN_WORKTREE/usr/tools`

#### Step 2: Build Julia with ASAN

Vérifiez un worktree Git (ou créez un répertoire de construction hors arbre) à `$BUILD_WORKTREE` et créez un fichier de configuration `$BUILD_WORKTREE/Make.user` avec

```
TOOLCHAIN=$(TOOLCHAIN_WORKTREE)/usr/tools

# use our new toolchain
USECLANG=1
override CC=$(TOOLCHAIN)/clang
override CXX=$(TOOLCHAIN)/clang++
export ASAN_SYMBOLIZER_PATH=$(TOOLCHAIN)/llvm-symbolizer

USE_BINARYBUILDER_LLVM=1

override SANITIZE=1
override SANITIZE_ADDRESS=1

# make the GC use regular malloc/frees, which are hooked by ASAN
override WITH_GC_DEBUG_ENV=1

# default to a debug build for better line number reporting
override JULIA_BUILD_MODE=debug

# make ASAN consume less memory
export ASAN_OPTIONS=detect_leaks=0:fast_unwind_on_malloc=0:allow_user_segv_handler=1:malloc_context_size=2

JULIA_PRECOMPILE=1

# tell libblastrampoline to not use RTLD_DEEPBIND
export LBT_USE_RTLD_DEEPBIND=0
```

Exécuter :

```sh
cd $BUILD_WORKTREE
make debug
```

pour construire `julia-debug` avec ASAN.

## Memory Sanitizer (MSAN)

Pour détecter l'utilisation de mémoire non initialisée, vous pouvez utiliser Clang's [memory sanitizer (MSAN)](https://clang.llvm.org/docs/MemorySanitizer.html) en compilant avec `SANITIZE_MEMORY=1`.

## Thread Sanitizer (TSAN)

Pour déboguer les conditions de course de données et d'autres problèmes liés aux threads, vous pouvez utiliser Clang's [thread sanitizer (TSAN)](https://clang.llvm.org/docs/ThreadSanitizer.html) en compilant avec `SANITIZE_THREAD=1`.
