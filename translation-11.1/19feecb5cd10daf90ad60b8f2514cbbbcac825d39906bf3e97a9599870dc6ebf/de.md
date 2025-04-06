# Sanitizer support

[Sanitizers](https://github.com/google/sanitizers) kann in benutzerdefinierten Julia-Bauten verwendet werden, um es einfacher zu machen, bestimmte Arten von Fehlern im internen C/C++-Code von Julia zu erkennen.

## Address Sanitizer: easy build

Aus einem Quell-Checkout von Julia sollten Sie in der Lage sein, eine Version zu erstellen, die die Adresssanitierung in Julia und LLVM unterstützt, wie folgt:

```sh
$ mkdir /tmp/julia
$ contrib/asan/build.sh /tmp/julia/
```

Hier haben wir `/tmp/julia` als Build-Verzeichnis gewählt, aber Sie können wählen, was immer Sie möchten. Nach dem Build führen Sie die Arbeitslast aus, die Sie mit `/tmp/julia/julia` testen möchten. Speicherfehler führen zu Fehlern.

Wenn Sie Anpassungen oder weitere Details benötigen, siehe die Dokumentation unten.

## General considerations

Die Verwendung von Clangs Sanitizern erfordert offensichtlich, dass Sie Clang verwenden (`USECLANG=1`), aber es gibt einen weiteren Haken: Die meisten Sanitizer benötigen eine Laufzeitbibliothek, die vom Host-Compiler bereitgestellt wird, während der instrumentierte Code, der von Julias JIT generiert wird, auf Funktionen dieser Bibliothek angewiesen ist. Das bedeutet, dass die LLVM-Version Ihres Host-Compilers mit der LLVM-Bibliothek übereinstimmen muss, die innerhalb von Julia verwendet wird.

Eine einfache Lösung besteht darin, einen dedizierten Build-Ordner zu haben, um ein passendes Toolchain bereitzustellen, indem Sie mit `BUILD_LLVM_CLANG=1` bauen. Sie können dann auf dieses Toolchain von einem anderen Build-Ordner aus verweisen, indem Sie `USECLANG=1` angeben und die Variablen `CC` und `CXX` überschreiben.

Die Sanitizer geben einen Fehler aus, wenn sie eine gemeinsam genutzte Bibliothek erkennen, die mit `RTLD_DEEPBIND` geöffnet wird (siehe: [google/sanitizers#611](https://github.com/google/sanitizers/issues/611)). Da [libblastrampoline](https://github.com/staticfloat/libblastrampoline) standardmäßig `RTLD_DEEPBIND` verwendet, müssen wir die Umgebungsvariable `LBT_USE_RTLD_DEEPBIND=0` setzen, wenn wir einen Sanitizer verwenden.

Um einen der Sanitizer zu verwenden, setzen Sie `SANITIZE=1` und dann das entsprechende Flag für den gewünschten Sanitizer.

Auf macOS könnte es erforderlich sein, einige zusätzliche Flags zu verwenden, damit es funktioniert. Insgesamt könnte es so aussehen, plus eines oder mehr der unten aufgeführten `SANITIZE_*` Flags:

```
make -C deps USE_BINARYBUILDER_LLVM=0 LLVM_VER=svn stage-llvm

make -C src SANITIZE=1 USECLANG=1 \
    CC=~+/deps/scratch/llvm-svn/build_Release/bin/clang \
    CXX=~+/deps/scratch/llvm-svn/build_Release/bin/clang++ \
    CPPFLAGS="-isysroot $(xcode-select -p)/Platforms/MacOSX.platform/Developer/SDKs/MacOSX.sdk" \
    CXXFLAGS="-isystem $(xcode-select -p)/Toolchains/XcodeDefault.xctoolchain/usr/include/c++/v1"
```

(oder füge diese in deine `Make.user` ein, damit du sie nicht jedes Mal merken musst).

## Address Sanitizer (ASAN)

Um Speicherfehler zu erkennen oder zu debuggen, können Sie Clangs [address sanitizer (ASAN)](https://clang.llvm.org/docs/AddressSanitizer.html) verwenden. Durch das Kompilieren mit `SANITIZE_ADDRESS=1` aktivieren Sie ASAN für den Julia-Compiler und den generierten Code. Darüber hinaus können Sie `LLVM_SANITIZE=1` angeben, um auch die LLVM-Bibliothek zu sanitieren. Beachten Sie, dass diese Optionen hohe Leistungs- und Speicherkosten verursachen. Zum Beispiel dauert die Verwendung von ASAN für Julia und LLVM `testall1` 8-10 Mal so lange und benötigt 20 Mal so viel Speicher (dies kann durch die Verwendung der unten beschriebenen Optionen auf einen Faktor von 3 und 4 reduziert werden).

Standardmäßig setzt Julia das ASAN-Flag `allow_user_segv_handler=1`, das erforderlich ist, damit die Signalübertragung ordnungsgemäß funktioniert. Sie können andere Optionen mit dem Umgebungsflag `ASAN_OPTIONS` definieren, in diesem Fall müssen Sie die zuvor erwähnte Standardoption wiederholen. Zum Beispiel kann der Speicherverbrauch reduziert werden, indem `fast_unwind_on_malloc=0` und `malloc_context_size=2` angegeben werden, was jedoch auf Kosten der Genauigkeit des Backtraces geht. Derzeit setzt Julia auch `detect_leaks=0`, aber dies sollte in Zukunft entfernt werden.

### Example setup

#### Step 1: Install toolchain

Checkout ein Git-Arbeitsbaum (oder erstellen Sie ein Verzeichnis für den Build außerhalb des Baums) unter `$TOOLCHAIN_WORKTREE` und erstellen Sie eine Konfigurationsdatei `$TOOLCHAIN_WORKTREE/Make.user` mit

```
USE_BINARYBUILDER_LLVM=1
BUILD_LLVM_CLANG=1
```

Führen:

```sh
cd $TOOLCHAIN_WORKTREE
make -C deps install-llvm install-clang install-llvm-tools
```

um die Toolchain-Binärdateien in `$TOOLCHAIN_WORKTREE/usr/tools` zu installieren

#### Step 2: Build Julia with ASAN

Checkout ein Git-Arbeitsbaum (oder erstellen Sie ein Verzeichnis für den Build außerhalb des Baums) unter `$BUILD_WORKTREE` und erstellen Sie eine Konfigurationsdatei `$BUILD_WORKTREE/Make.user` mit

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

Führen:

```sh
cd $BUILD_WORKTREE
make debug
```

`julia-debug` mit ASAN erstellen.

## Memory Sanitizer (MSAN)

Um die Verwendung von nicht initialisiertem Speicher zu erkennen, können Sie Clangs [memory sanitizer (MSAN)](https://clang.llvm.org/docs/MemorySanitizer.html) verwenden, indem Sie mit `SANITIZE_MEMORY=1` kompilieren.

## Thread Sanitizer (TSAN)

Für das Debuggen von Datenrennen und anderen threadingbezogenen Problemen können Sie Clangs [thread sanitizer (TSAN)](https://clang.llvm.org/docs/ThreadSanitizer.html) verwenden, indem Sie mit `SANITIZE_THREAD=1` kompilieren.
