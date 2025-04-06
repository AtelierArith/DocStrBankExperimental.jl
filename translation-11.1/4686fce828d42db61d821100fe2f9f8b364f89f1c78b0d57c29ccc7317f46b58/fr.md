# Windows

Ce fichier décrit comment installer, ou construire, et utiliser Julia sur Windows.

Pour plus d'informations générales sur Julia, veuillez consulter le [main README](https://github.com/JuliaLang/julia/blob/master/README.md) ou le [documentation](https://docs.julialang.org).

## General Information for Windows

Nous recommandons vivement d'exécuter Julia en utilisant une application de terminal moderne, en particulier Windows Terminal, qui peut être installé à partir de [Microsoft Store](https://aka.ms/terminal).

### Line endings

Julia utilise exclusivement des fichiers en mode binaire. Contrairement à de nombreux autres programmes Windows, si vous écrivez `\n` dans un fichier, vous obtenez un `\n` dans le fichier, et non un autre motif de bits. Cela correspond au comportement observé par d'autres systèmes d'exploitation. Si vous avez installé Git pour Windows, il est suggéré, mais pas obligatoire, de configurer votre Git système pour utiliser la même convention :

```sh
git config --global core.eol lf
git config --global core.autocrlf input
```

ou modifiez `%USERPROFILE%\.gitconfig` et ajoutez/modifiez les lignes :

```
[core]
    eol = lf
    autocrlf = input
```

## Binary distribution

Pour les notes d'installation de la distribution binaire sur Windows, veuillez consulter les instructions à [https://julialang.org/downloads/platform/#windows](https://julialang.org/downloads/platform/#windows).

## Source distribution

### Cygwin-to-MinGW cross-compiling

La méthode recommandée pour compiler Julia à partir des sources sur Windows est de le faire par cross-compilation depuis [Cygwin](https://www.cygwin.com), en utilisant les versions des compilateurs MinGW-w64 disponibles via le gestionnaire de paquets de Cygwin.

1. Téléchargez et exécutez le programme d'installation de Cygwin pour [32 bit](https://cygwin.com/setup-x86.exe) ou [64 bit](https://cygwin.com/setup-x86_64.exe). Notez que vous pouvez compiler soit Julia 32 bits soit 64 bits à partir de Cygwin 32 bits ou 64 bits. Cygwin 64 bits a une sélection de paquets légèrement plus petite mais souvent plus à jour.

    *Avancé* : vous pouvez sauter les étapes 2 à 4 en exécutant :

    ```sh
    setup-x86_64.exe -s <url> -q -P cmake,gcc-g++,git,make,patch,curl,m4,python3,p7zip,mingw64-i686-gcc-g++,mingw64-i686-gcc-fortran,mingw64-x86_64-gcc-g++,mingw64-x86_64-gcc-fortran
    ```

    remplacer `<url>` par un site de [https://cygwin.com/mirrors.html](https://cygwin.com/mirrors.html) ou exécutez d'abord la configuration manuellement et sélectionnez un miroir.
2. Sélectionnez l'emplacement d'installation et un miroir à partir duquel télécharger.
3. À l'étape *Sélectionner les paquets*, sélectionnez ce qui suit :

    1. De la catégorie *Devel* : `cmake`, `gcc-g++`, `git`, `make`, `patch`
    2. De la catégorie *Net* : `curl`
    3. De la catégorie *Interpréteurs* (ou *Python*) : `m4`, `python3`
    4. De la catégorie *Archive* : `p7zip`
    5. Pour Julia 32 bits, et également de la catégorie *Devel* : `mingw64-i686-gcc-g++` et `mingw64-i686-gcc-fortran`
    6. Pour Julia 64 bits, et également de la catégorie *Devel* :  `mingw64-x86_64-gcc-g++` et `mingw64-x86_64-gcc-fortran`
4. Laissez l'installation de Cygwin se terminer, puis démarrez à partir du raccourci installé *'Cygwin Terminal'*, ou *'Cygwin64 Terminal'*, respectivement.
5. Construire Julia et ses dépendances à partir des sources :

    1. Obtenez les sources de Julia

        ```sh
        git clone https://github.com/JuliaLang/julia.git
        cd julia
        ```

        Astuce : Si vous obtenez une `erreur : impossible de fork() pour fetch-pack : Ressource temporairement indisponible` de git, ajoutez `alias git="env PATH=/usr/bin git"` à `~/.bashrc` et redémarrez Cygwin.
    2. Définissez la variable `XC_HOST` dans `Make.user` pour indiquer la compilation croisée MinGW-w64.

        ```sh
        echo 'XC_HOST = i686-w64-mingw32' > Make.user     # for 32 bit Julia
        # or
        echo 'XC_HOST = x86_64-w64-mingw32' > Make.user   # for 64 bit Julia
        ```
    3. Commencer la construction

        ```sh
        make -j 4       # Adjust the number of threads (4) to match your build environment.
        make -j 4 debug # This builds julia-debug.exe
        ```
6. Exécutez Julia en utilisant directement les exécutables Julia

    ```sh
    usr/bin/julia.exe
    usr/bin/julia-debug.exe
    ```

!!! note "Pro tip: build both!"
    ```sh
    make O=julia-win32 configure
    make O=julia-win64 configure
    echo 'XC_HOST = i686-w64-mingw32' > julia-win32/Make.user
    echo 'XC_HOST = x86_64-w64-mingw32' > julia-win64/Make.user
    echo 'ifeq ($(BUILDROOT),$(JULIAHOME))
            $(error "in-tree build disabled")
          endif' >> Make.user
    make -C julia-win32  # build for Windows x86 in julia-win32 folder
    make -C julia-win64  # build for Windows x86-64 in julia-win64 folder
    ```


### Compiling with MinGW/MSYS2

[MSYS2](https://www.msys2.org/) est un environnement de distribution et de construction de logiciels pour Windows.

Remarque : MSYS2 nécessite **Windows 7 64 bits** ou une version plus récente.

1. Installer et configurer MSYS2.

    1. Téléchargez et exécutez le dernier installateur pour la distribution [64-bit](https://github.com/msys2/msys2-installer/releases/latest). L'installateur aura un nom comme `msys2-x86_64-yyyymmdd.exe`.
    2. Ouvrez le shell MSYS2. Mettez à jour la base de données des paquets et les paquets de base :

        `pacman -Syu`
    3. Quitter et redémarrer MSYS2. Mettre à jour le reste des paquets de base :

        `pacman -Syu`
    4. Ensuite, installez les outils nécessaires pour construire julia :

        `pacman -S cmake diffutils git m4 make patch tar p7zip curl python`

        Pour Julia 64 bits, installez la version x86_64 :

        `pacman -S mingw-w64-x86_64-gcc`

        Pour Julia 32 bits, installez la version i686 :

        `pacman -S mingw-w64-i686-gcc`
    5. La configuration de MSYS2 est terminée. Maintenant, `quitter` le shell MSYS2.
2. Construire Julia et ses dépendances avec des dépendances pré-construites.

    1. Ouvrez un nouveau [**MINGW64/MINGW32 shell**](https://www.msys2.org/docs/environments/#overview). Actuellement, nous ne pouvons pas utiliser à la fois mingw32 et mingw64, donc si vous souhaitez construire les versions x86_64 et i686, vous devrez les construire dans chaque environnement séparément.
    2. Clonez les sources de Julia :

        `git clone https://github.com/JuliaLang/julia.git  cd julia`
    3. Commencer la construction

        `make -j$(nproc)`

!!! note "Pro tip: build in dir"
    ```sh
    make O=julia-mingw-w64 configure
    echo 'ifeq ($(BUILDROOT),$(JULIAHOME))
            $(error "in-tree build disabled")
          endif' >> Make.user
    make -C julia-mingw-w64
    ```


### Cross-compiling from Unix (Linux/Mac/WSL)

Vous pouvez également utiliser des compilateurs croisés MinGW-w64 pour construire une version Windows de Julia à partir de Linux, Mac ou du Sous-système Windows pour Linux (WSL).

Tout d'abord, vous devez vous assurer que votre système dispose des dépendances requises. Nous avons besoin de wine (>=1.7.5), d'un compilateur système et de quelques téléchargeurs. Remarque : une installation de Cygwin pourrait interférer avec cette méthode si vous utilisez WSL.

**Sur Ubuntu** (sur d'autres systèmes Linux, les noms des dépendances sont susceptibles d'être similaires) :

```sh
apt-get install wine-stable gcc wget p7zip-full winbind mingw-w64 gfortran-mingw-w64
dpkg --add-architecture i386 && apt-get update && apt-get install wine32 # add sudo to each if needed
# switch all of the following to their "-posix" variants (interactively):
for pkg in i686-w64-mingw32-g++ i686-w64-mingw32-gcc i686-w64-mingw32-gfortran x86_64-w64-mingw32-g++ x86_64-w64-mingw32-gcc x86_64-w64-mingw32-gfortran; do
    sudo update-alternatives --config $pkg
done
```

**Sur Mac** : Installez XCode, les outils en ligne de commande XCode, X11 (maintenant [XQuartz](https://www.xquartz.org/)), et [MacPorts](https://www.macports.org/install.php) ou [Homebrew](https://brew.sh/). Ensuite, exécutez `port install wine wget mingw-w64`, ou `brew install wine wget mingw-w64`, selon le cas.

**Puis exécutez la construction :**

1. `git clone https://github.com/JuliaLang/julia.git julia-win32`
2. `cd julia-win32`
3. `echo override XC_HOST = i686-w64-mingw32 >> Make.user`
4. `faire`
5. `make win-extras` (Nécessaire avant d'exécuter `make binary-dist`)
6. `make binary-dist` puis `make exe` pour créer l'installateur Windows.
7. déplacez l'installateur `julia-*.exe` vers la machine cible

Si vous construisez pour Windows 64 bits, les étapes sont essentiellement les mêmes. Il suffit de remplacer `i686` dans `XC_HOST` par `x86_64`. (Remarque : sur Mac, wine ne fonctionne qu'en mode 32 bits).

## Debugging a cross-compiled build under wine

La manière la plus efficace de déboguer une version cross-compilée de Julia sur l'hôte de cross-compilation est d'installer une version Windows de GDB et de l'exécuter sous wine comme d'habitude. Les paquets préconstruits disponibles [as part of the MSYS2 project](https://packages.msys2.org/) sont connus pour fonctionner. En plus du paquet GDB, vous pourriez également avoir besoin des paquets python et termcap. Enfin, l'invite de GDB peut ne pas fonctionner lorsqu'elle est lancée depuis la ligne de commande. Cela peut être contourné en préfixant `wineconsole` à l'invocation régulière de GDB.

## After compiling

Compiler en utilisant l'une des options ci-dessus crée une version de base de Julia, mais pas certains composants supplémentaires qui sont inclus si vous exécutez l'installateur binaire complet de Julia. Si vous avez besoin de ces composants, le moyen le plus simple de les obtenir est de construire l'installateur vous-même en utilisant `make win-extras` suivi de `make binary-dist` et `make exe`. Ensuite, exécutez l'installateur résultant.

## Windows Build Debugging

### GDB hangs with Cygwin mintty

  * Exécutez GDB sous la console Windows (cmd) à la place. GDB [may not function properly](https://www.cygwin.com/ml/cygwin/2009-02/msg00531.html) sous mintty avec des applications non-Cygwin. Vous pouvez utiliser `cmd /c start` pour démarrer la console Windows depuis mintty si nécessaire.

### GDB not attaching to the right process

  * Utilisez le PID du gestionnaire de tâches Windows ou `WINPID` de la commande `ps` au lieu du PID des outils de ligne de commande de style Unix (par exemple, `pgrep`). Vous devrez peut-être ajouter la colonne PID si elle n'est pas affichée par défaut dans le gestionnaire de tâches Windows.

### GDB not showing the right backtrace

  * Lorsque vous vous attachez au processus julia, GDB peut ne pas s'attacher au bon thread. Utilisez la commande `info threads` pour afficher tous les threads et `thread <threadno>` pour changer de thread.
  * Assurez-vous d'utiliser une version 32 bits de GDB pour déboguer une version 32 bits de Julia, ou une version 64 bits de GDB pour déboguer une version 64 bits de Julia.

### Build process is slow/eats memory/hangs my computer

  * Désactivez les services Windows [Superfetch](https://en.wikipedia.org/wiki/Windows_Vista_I/O_technologies#SuperFetch) et [Program Compatibility Assistant](https://blogs.msdn.com/b/cjacks/archive/2011/11/22/managing-the-windows-7-program-compatibility-assistant-pca.aspx), car ils sont connus pour avoir [spurious interactions](https://cygwin.com/ml/cygwin/2011-12/msg00058.html) avec MinGW/Cygwin.

    Comme mentionné dans le lien ci-dessus : une utilisation excessive de la mémoire par `svchost` peut être examinée dans le Gestionnaire des tâches en cliquant sur le processus `svchost.exe` à forte consommation de mémoire et en sélectionnant `Aller aux services`. Désactivez les services enfants un par un jusqu'à ce qu'un coupable soit trouvé.
  * Attention à [BLODA](https://cygwin.com/faq/faq.html#faq.using.bloda). L'outil [vmmap](https://technet.microsoft.com/en-us/sysinternals/dd535533.aspx) est indispensable pour identifier de tels conflits logiciels. Utilisez vmmap pour inspecter la liste des DLL chargées pour bash, mintty ou un autre processus persistant utilisé pour conduire la construction. Essentiellement, *toute* DLL en dehors du répertoire système Windows est un potentiel BLODA.
