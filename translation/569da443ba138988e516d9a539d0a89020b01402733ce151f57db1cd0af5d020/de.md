# Building Julia (Detailed)

## Downloading the Julia source code

Wenn Sie hinter einer Firewall sind, müssen Sie möglicherweise das `https`-Protokoll anstelle des `git`-Protokolls verwenden:

```sh
git config --global url."https://".insteadOf git://
```

Stellen Sie sicher, dass Sie Ihr System auch so konfigurieren, dass die entsprechenden Proxy-Einstellungen verwendet werden, z. B. durch Festlegen der Variablen `https_proxy` und `http_proxy`.

## Building Julia

Beim ersten Kompilieren wird das Build automatisch die vorgefertigte [external dependencies](#Required-Build-Tools-and-External-Libraries) herunterladen. Wenn Sie alle Abhängigkeiten selbst erstellen möchten oder auf einem System bauen, das während des Build-Prozesses keinen Netzwerkzugang hat, fügen Sie Folgendes in `Make.user` hinzu:

```
USE_BINARYBUILDER=0
```

Der Bau von Julia erfordert 5 GiB, wenn alle Abhängigkeiten gebaut werden, und ungefähr 4 GiB virtuellen Speicher.

Um einen parallelen Build durchzuführen, verwenden Sie `make -j N` und geben Sie die maximale Anzahl gleichzeitiger Prozesse an. Wenn die Standardwerte im Build für Sie nicht funktionieren und Sie spezifische Make-Parameter festlegen müssen, können Sie diese in `Make.user` speichern und die Datei im Stammverzeichnis Ihres Julia-Quellcodes ablegen. Der Build überprüft automatisch die Existenz von `Make.user` und verwendet sie, wenn sie vorhanden ist.

Sie können Out-of-Tree-Bauten von Julia erstellen, indem Sie `make O=<build-directory> configure` in der Befehlszeile angeben. Dies erstellt ein Verzeichnis-Mirror mit allen notwendigen Makefiles, um Julia im angegebenen Verzeichnis zu bauen. Diese Builds teilen sich die Quellcodedateien in Julia und `deps/srccache`. Jedes Out-of-Tree-Bauverzeichnis kann seine eigene `Make.user`-Datei haben, um die globale `Make.user`-Datei im obersten Verzeichnis zu überschreiben.

Wenn alles korrekt funktioniert, sehen Sie ein Julia-Banner und eine interaktive Eingabeaufforderung, in die Sie Ausdrücke zur Auswertung eingeben können. (Fehler, die mit Bibliotheken zusammenhängen, können durch alte, inkompatible Bibliotheken verursacht werden, die in Ihrem PATH vorhanden sind. In diesem Fall versuchen Sie, das `julia`-Verzeichnis früher im PATH zu platzieren). Beachten Sie, dass die meisten der oben genannten Anweisungen für Unix-Systeme gelten.

Um Julia von überall aus auszuführen, können Sie:

  * füge ein Alias hinzu (in `bash`: `echo "alias julia='/path/to/install/folder/bin/julia'" >> ~/.bashrc && source ~/.bashrc`), oder
  * füge einen symbolischen Link zur `julia`-Ausführungsdatei im `julia`-Verzeichnis zu `/usr/local/bin` (oder einem anderen geeigneten Verzeichnis, das bereits in deinem Pfad ist) hinzu, oder
  * füge das Verzeichnis `julia` zu deinem ausführbaren Pfad für diese Shell-Sitzung hinzu (in `bash`: `export PATH="$(pwd):$PATH"` ; in `csh` oder `tcsh`:

`set path= ( $path $cwd )` ), oder

  * füge das Verzeichnis `julia` dauerhaft zu deinem ausführbaren Pfad hinzu (z. B. in `.bash_profile`), oder
  * Schreibe `prefix=/path/to/install/folder` in `Make.user` und führe dann `make install` aus. Wenn bereits eine Version von Julia in diesem Ordner installiert ist, solltest du sie löschen, bevor du `make install` ausführst.

Einige der Optionen, die Sie festlegen können, um den Build von Julia zu steuern, sind am Anfang der Datei `Make.inc` aufgeführt und dokumentiert, aber Sie sollten diese niemals zu diesem Zweck bearbeiten, verwenden Sie stattdessen `Make.user`.

Julias Makefiles definieren praktische automatische Regeln namens `print-<VARNAME>`, um den Wert von Variablen auszugeben, wobei `<VARNAME>` durch den Namen der Variablen ersetzt wird, deren Wert ausgegeben werden soll. Zum Beispiel

```console
$ make print-JULIA_PRECOMPILE
JULIA_PRECOMPILE=1
```

Diese Regeln sind nützlich für Debugging-Zwecke.

Jetzt solltest du in der Lage sein, Julia so auszuführen:

```
julia
```

Wenn Sie ein Julia-Paket für die Verteilung auf Linux, macOS oder Windows erstellen, werfen Sie einen Blick auf die detaillierten Hinweise in [distributing.md](https://github.com/JuliaLang/julia/blob/master/doc/src/devdocs/build/distributing.md).

## Updating an existing source tree

Wenn Sie `julia` zuvor mit `git clone` heruntergeladen haben, können Sie den vorhandenen Quellbaum mit `git pull` aktualisieren, anstatt neu zu beginnen:

```sh
cd julia
git pull && make
```

Angenommen, Sie haben keine Änderungen am Quellbaum vorgenommen, die mit den Updates des Upstreams in Konflikt stehen, werden diese Befehle einen Build auslösen, um auf die neueste Version zu aktualisieren.

## General troubleshooting

1. Im Laufe der Zeit kann die Basisbibliothek so viele Änderungen ansammeln, dass der Bootstrapping-Prozess beim Erstellen des Systemabbilds fehlschlägt. Wenn dies geschieht, kann der Build mit einem Fehler wie

    ```sh
     *** This error is usually fixed by running 'make clean'. If the error persists, try 'make cleanall' ***
    ```

    Wie beschrieben, ist das Ausführen von `make clean && make` normalerweise ausreichend. Gelegentlich ist die gründlichere Bereinigung durch `make cleanall` erforderlich.
2. Neue Versionen externer Abhängigkeiten können eingeführt werden, die gelegentlich Konflikte mit bestehenden Builds älterer Versionen verursachen können.

    a. Spezielle `make`-Ziele existieren, um den bestehenden Build einer Abhängigkeit zu löschen. Zum Beispiel wird `make -C deps clean-llvm` den bestehenden Build von `llvm` bereinigen, sodass `llvm` beim nächsten Aufruf von `make` aus der heruntergeladenen Quellverteilung neu erstellt wird. `make -C deps distclean-llvm` ist eine stärkere Löschung, die auch die heruntergeladene Quellverteilung löscht, um sicherzustellen, dass eine frische Kopie der Quellverteilung heruntergeladen wird und dass alle neuen Patches beim nächsten Aufruf von `make` angewendet werden.

    b. Um vorhandene Binaries von `julia` und all seinen Abhängigkeiten zu löschen, löschen Sie das Verzeichnis `./usr` *im Quellbaum*.
3. Wenn Sie macOS kürzlich aktualisiert haben, stellen Sie sicher, dass Sie `xcode-select --install` ausführen, um die Befehlszeilenwerkzeuge zu aktualisieren. Andernfalls könnten Sie auf Fehler wegen fehlender Header und Bibliotheken stoßen, wie z. B. `ld: library not found for -lcrt1.10.6.o`.
4. Wenn Sie das Quellverzeichnis verschoben haben, könnten Sie Fehler wie `CMake Error: The current CMakeCache.txt directory ... is different than the directory ... where CMakeCache.txt was created.` erhalten, in diesem Fall können Sie die störende Abhängigkeit unter `deps` löschen.
5. In extremen Fällen möchten Sie möglicherweise den Quellbaum in einen makellosen Zustand zurücksetzen. Die folgenden Git-Befehle können hilfreich sein:

    ```sh
     git reset --hard #Forcibly remove any changes to any files under version control
     git clean -x -f -d #Forcibly remove any file or directory not under version control
    ```

    *Um zu vermeiden, dass Arbeit verloren geht, stellen Sie sicher, dass Sie wissen, was diese Befehle tun, bevor Sie sie ausführen. `git` wird in der Lage sein, diese Änderungen nicht rückgängig zu machen!*

## Platform-Specific Notes

Notizen für verschiedene Betriebssysteme:

  * [Linux](https://github.com/JuliaLang/julia/blob/master/doc/src/devdocs/build/linux.md)
  * [macOS](https://github.com/JuliaLang/julia/blob/master/doc/src/devdocs/build/macos.md)
  * [Windows](https://github.com/JuliaLang/julia/blob/master/doc/src/devdocs/build/windows.md)
  * [FreeBSD](https://github.com/JuliaLang/julia/blob/master/doc/src/devdocs/build/freebsd.md)

Notizen für verschiedene Architekturen:

  * [ARM](https://github.com/JuliaLang/julia/blob/master/doc/src/devdocs/build/arm.md)

## Required Build Tools and External Libraries

Der Bau von Julia erfordert, dass die folgende Software installiert ist:

  * **[GNU make]**                — Abhängigkeiten erstellen.
  * **[gcc & g++][gcc]** (>= 7.1) oder **[Clang][clang]** (>= 5.0, >= 9.3 für Apple Clang) — Kompilieren und Verlinken von C, C++.
  * **[libatomic][gcc]**          — bereitgestellt von **[gcc]** und benötigt, um atomare Operationen zu unterstützen.
  * **[python]** (>=2.7)          — benötigt, um LLVM zu erstellen.
  * **[gfortran]**                — Kompilieren und Verlinken von Fortran-Bibliotheken.
  * **[perl]**                    — Vorverarbeitung von Header-Dateien von Bibliotheken.
  * **[wget]**, **[curl]** oder **[fetch]** (FreeBSD) — um automatisch externe Bibliotheken herunterzuladen.
  * **[m4]**                      — benötigt, um GMP zu erstellen.
  * **[awk]**                     — Hilfswerkzeug für Makefiles.
  * **[Patch]**                   — zum Ändern von Quellcode.
  * **[cmake]** (>= 3.4.3)        — benötigt, um `libgit2` zu bauen.
  * **[pkg-config]**              — benötigt, um `libgit2` korrekt zu bauen, insbesondere für die Proxy-Unterstützung.
  * **[powershell]** (>= 3.0)     — nur notwendig unter Windows.
  * **[welches]**                   — benötigt, um Build-Abhängigkeiten zu überprüfen.

Auf Debian-basierten Distributionen (z. B. Ubuntu) können Sie sie einfach mit `apt-get` installieren:

```
sudo apt-get install build-essential libatomic1 python gfortran perl wget m4 cmake pkg-config curl
```

Julia verwendet die folgenden externen Bibliotheken, die automatisch heruntergeladen (oder in einigen Fällen im Julia-Quellcode-Repository enthalten) und dann beim ersten Ausführen von `make` aus dem Quellcode kompiliert werden. Die spezifischen Versionsnummern dieser Bibliotheken, die Julia verwendet, sind in [`deps/$(libname).version`](https://github.com/JuliaLang/julia/blob/master/deps/) aufgeführt:

  * **[LLVM]** (15.0 + [patches](https://github.com/JuliaLang/llvm-project/tree/julia-release/15.x)) — Compiler-Infrastruktur (siehe [note below](#llvm)).
  * **[FemtoLisp]**            — verpackt mit Julia-Quellcode und verwendet, um die Compiler-Frontend zu implementieren.
  * **[libuv]**  (benutzerdefinierter Fork) — tragbare, leistungsstarke, ereignisbasierte I/O-Bibliothek.
  * **[OpenLibm]**             — portable libm-Bibliothek mit grundlegenden mathematischen Funktionen.
  * **[DSFMT]**                — schnelle Mersenne Twister Pseudorandom-Zahlengenerator-Bibliothek.
  * **[OpenBLAS]**             — schnell, offen und gewartet [Basis-Linear-Algebra-Unterprogramme (BLAS)]
  * **[LAPACK]**               — Bibliothek von Routinen der linearen Algebra zur Lösung von Systemen simultaner linearer Gleichungen, Lösungen der kleinsten Quadrate von linearen Gleichungssystemen, Eigenwertproblemen und Problemen mit singulären Werten.
  * **[MKL]** (optional)       – OpenBLAS und LAPACK können durch Intels MKL-Bibliothek ersetzt werden.
  * **[SuiteSparse]**          — Bibliothek von linearen Algebra-Routinen für spärliche Matrizen.
  * **[PCRE]**                 — Perl-kompatible reguläre Ausdrücke Bibliothek.
  * **[GMP]**                  — GNU Mehrpräzisions-Arithmetikbibliothek, benötigt für die Unterstützung von `BigInt`.
  * **[MPFR]**                 — GNU-Bibliothek für mehrfache Präzision von Fließkommazahlen, benötigt für die Unterstützung von Fließkommazahlen mit beliebiger Präzision (`BigFloat`).
  * **[libgit2]**              — Git-verknüpfbare Bibliothek, die vom Paketmanager von Julia verwendet wird.
  * **[curl]**                 — libcurl bietet Download- und Proxy-Unterstützung.
  * **[libssh2]**              — Bibliothek für SSH-Transport, verwendet von libgit2 für Pakete mit SSH-Remotes.
  * **[mbedtls]**              — Bibliothek, die für Kryptographie und Transportschichtsicherheit verwendet wird, verwendet von libssh2
  * **[utf8proc]**             — eine Bibliothek zur Verarbeitung von UTF-8-kodierten Unicode-Zeichenfolgen.
  * **[LLVM libunwind]** — LLVMs Fork von [libunwind], einer Bibliothek, die die Aufrufkette eines Programms bestimmt.
  * **[ITTAPI]**               — Intels Instrumentierungs- und Nachverfolgungstechnologie sowie Just-In-Time-API.

[GNU make]:     https://www.gnu.org/software/make [patch]:        https://www.gnu.org/software/patch [wget]:         https://www.gnu.org/software/wget [m4]:           https://www.gnu.org/software/m4 [awk]:          https://www.gnu.org/software/gawk [gcc]:          https://gcc.gnu.org [clang]:        https://clang.llvm.org [python]:       https://www.python.org/ [gfortran]:     https://gcc.gnu.org/fortran/ [curl]:         https://curl.haxx.se [fetch]:        https://www.freebsd.org/cgi/man.cgi?fetch(1) [perl]:         https://www.perl.org [cmake]:        https://www.cmake.org [OpenLibm]:     https://github.com/JuliaLang/openlibm [DSFMT]:        https://github.com/MersenneTwister-Lab/dSFMT [OpenBLAS]:     https://github.com/xianyi/OpenBLAS [LAPACK]:       https://www.netlib.org/lapack [MKL]:          https://software.intel.com/en-us/articles/intel-mkl [SuiteSparse]:  https://people.engr.tamu.edu/davis/suitesparse.html [PCRE]:         https://www.pcre.org [LLVM]:         https://www.llvm.org [LLVM libunwind]: https://github.com/llvm/llvm-project/tree/main/libunwind [FemtoLisp]:    https://github.com/JeffBezanson/femtolisp [GMP]:          https://gmplib.org [MPFR]:         https://www.mpfr.org [libuv]:        https://github.com/JuliaLang/libuv [libgit2]:      https://libgit2.org/ [utf8proc]:     https://julialang.org/utf8proc/ [libunwind]:    https://www.nongnu.org/libunwind [libssh2]:      https://www.libssh2.org [mbedtls]:      https://tls.mbed.org/ [pkg-config]:   https://www.freedesktop.org/wiki/Software/pkg-config/ [powershell]:   https://docs.microsoft.com/en-us/powershell/scripting/wmf/overview [which]:        https://carlowood.github.io/which/ [ITTAPI]:       https://github.com/intel/ittapi

## Build dependencies

Wenn Sie bereits eines oder mehrere dieser Pakete auf Ihrem System installiert haben, können Sie verhindern, dass Julia Duplikate dieser Bibliotheken kompiliert, indem Sie `USE_SYSTEM_...=1` an `make` übergeben oder die Zeile zu `Make.user` hinzufügen. Die vollständige Liste der möglichen Flags finden Sie in `Make.inc`.

Bitte beachten Sie, dass dieses Verfahren nicht offiziell unterstützt wird, da es zusätzliche Variabilität bei der Installation und Versionierung der Abhängigkeiten einführt und nur für Systempaketbetreuer empfohlen wird. Unerwartete Kompilierungsfehler können auftreten, da das Build-System keine weiteren Überprüfungen durchführt, um sicherzustellen, dass die richtigen Pakete installiert sind.

### LLVM

Die komplizierteste Abhängigkeit ist LLVM, für die wir zusätzliche Patches von upstream benötigen (LLVM ist nicht rückwärtskompatibel).

Für die Verpackung von Julia mit LLVM empfehlen wir entweder:

  * ein Julia-eigenes LLVM-Bibliothek in das Julia-Paket einbinden, oder
  * Hinzufügen der Patches zum LLVM-Paket der Distribution.

      * Eine vollständige Liste der Patches ist verfügbar unter [Github](https://github.com/JuliaLang/llvm-project), siehe den Branch `julia-release/15.x`.
      * Der einzige Julia-spezifische Patch ist das Umbenennen der Bibliothek (`llvm7-symver-jlprefix.patch`), der *nicht* auf ein System-LLVM angewendet werden sollte.
      * Die verbleibenden Patches sind alle upstream-Bugfixes und wurden in das upstream LLVM integriert.

Die Verwendung einer nicht gepatchten oder einer anderen Version von LLVM führt zu Fehlern und/oder schlechter Leistung. Sie können eine andere Version von LLVM aus einem entfernten Git-Repository mit den folgenden Optionen in der `Make.user`-Datei erstellen:

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

Die verschiedenen Build-Phasen werden durch spezifische Dateien gesteuert:

  * `deps/llvm.version` : berühren oder ändern, um eine neue Version auszuchecken, `make get-llvm check-llvm`
  * `deps/srccache/llvm/source-extracted` : Ergebnis von `make extract-llvm`
  * `deps/llvm/build_Release*/build-configured` : Ergebnis von `make configure-llvm`
  * `deps/llvm/build_Release*/build-configured` : Ergebnis von `make compile-llvm`
  * `usr-staging/llvm/build_Release*.tgz` : Ergebnis von `make stage-llvm` (erneuern mit `make reinstall-llvm`)
  * `usr/manifest/llvm` : Ergebnis von `make install-llvm` (erneuern mit `make uninstall-llvm`)
  * `make version-check-llvm` : wird jedes Mal ausgeführt, um den Benutzer zu warnen, wenn es lokale Änderungen gibt.

Obwohl Julia mit neueren LLVM-Versionen erstellt werden kann, sollte die Unterstützung dafür als experimentell angesehen werden und ist nicht für die Verpackung geeignet.

### libuv

Julia verwendet einen benutzerdefinierten Fork von libuv. Es ist eine kleine Abhängigkeit und kann sicher im selben Paket wie Julia gebündelt werden, ohne mit der Systembibliothek in Konflikt zu geraten. Julia-Bauten sollten *nicht* versuchen, die System-libuv zu verwenden.

### BLAS and LAPACK

Als eine leistungsstarke numerische Sprache sollte Julia mit einer mehrthreadigen BLAS und LAPACK verbunden werden, wie OpenBLAS oder ATLAS, die eine viel bessere Leistung bieten als die Referenzimplementierungen `libblas`, die möglicherweise standardmäßig auf einigen Systemen vorhanden sind.

## Source distributions of releases

Jede Vorabversion und Veröffentlichung von Julia hat eine "vollständige" Quellverteilung und eine "leichte" Quellverteilung.

Die vollständige Quellverteilung enthält den Quellcode für Julia und alle Abhängigkeiten, sodass sie ohne Internetverbindung aus dem Quellcode erstellt werden kann. Die leichte Quellverteilung enthält nicht den Quellcode der Abhängigkeiten.

Zum Beispiel ist `julia-1.0.0.tar.gz` die Quellverteilung für die `v1.0.0`-Version von Julia, während `julia-1.0.0-full.tar.gz` die vollständige Quellverteilung ist.

## Building Julia from source with a Git checkout of a stdlib

Wenn Sie Julia aus dem Quellcode mit einem Git-Checkout einer stdlib erstellen müssen, verwenden Sie `make DEPS_GIT=NAME_OF_STDLIB` beim Erstellen von Julia.

Wenn Sie beispielsweise Julia aus dem Quellcode mit einem Git-Checkout von Pkg erstellen müssen, verwenden Sie `make DEPS_GIT=Pkg` beim Erstellen von Julia. Das `Pkg`-Repository befindet sich in `stdlib/Pkg` und wurde ursprünglich mit einem abgetrennten `HEAD` erstellt. Wenn Sie dies aus einem bereits vorhandenen Julia-Repository tun, müssen Sie möglicherweise vorher `make clean` ausführen.

Wenn Sie Julia aus dem Quellcode mit Git-Checkouts von mehr als einer Standardbibliothek erstellen müssen, sollte `DEPS_GIT` eine durch Leerzeichen getrennte Liste der Standardbibliotheksnamen sein. Wenn Sie beispielsweise Julia aus dem Quellcode mit einem Git-Checkout von Pkg, Tar und Downloads erstellen müssen, verwenden Sie `make DEPS_GIT='Pkg Tar Downloads'` beim Erstellen von Julia.

## Building an "assert build" of Julia

Ein "Assert-Build" von Julia ist ein Build, der sowohl mit `FORCE_ASSERTIONS=1` als auch mit `LLVM_ASSERTIONS=1` erstellt wurde. Um einen Assert-Build zu erstellen, definieren Sie beide der folgenden Variablen in Ihrer `Make.user`-Datei:

```
FORCE_ASSERTIONS=1
LLVM_ASSERTIONS=1
```

Bitte beachten Sie, dass Assert-Bauten von Julia langsamer sein werden als reguläre (nicht-Assert) Bauten.

## Building 32-bit Julia on a 64-bit machine

Gelegentlich können spezifische Fehler in 32-Bit-Architekturen auftreten, und wenn dies geschieht, ist es nützlich, das Problem auf Ihrem lokalen Computer zu debuggen. Da die meisten modernen 64-Bit-Systeme die Ausführung von Programmen unterstützen, die für 32-Bit-Systeme erstellt wurden, können Sie wahrscheinlich eine 32-Bit-Version von Julia für Ihr System verwenden, die Sie von der [official downloads page](https://julialang.org/downloads/) erhalten können, wenn Sie Julia nicht aus dem Quellcode neu kompilieren müssen (z. B. wenn Sie hauptsächlich das Verhalten einer 32-Bit-Julia untersuchen möchten, ohne den C-Code berühren zu müssen). Wenn Sie jedoch Julia aus dem Quellcode neu kompilieren müssen, ist eine Möglichkeit, einen Docker-Container eines 32-Bit-Systems zu verwenden. Zumindest für jetzt ist es relativ einfach, eine 32-Bit-Version von Julia mit [ubuntu 32-bit docker images](https://hub.docker.com/r/i386/ubuntu) zu erstellen. Kurz gesagt, nachdem Sie `docker` eingerichtet haben, sind hier die erforderlichen Schritte:

```sh
$ docker pull i386/ubuntu
$ docker run --platform i386 -i -t i386/ubuntu /bin/bash
```

An diesem Punkt sollten Sie sich in einer 32-Bit-Maschinenkonsole befinden (beachten Sie, dass `uname` die Host-Architektur meldet und weiterhin 64-Bit anzeigt, dies hat jedoch keinen Einfluss auf den Julia-Build). Sie können Pakete hinzufügen und Code kompilieren; wenn Sie `exit` eingeben, gehen alle Änderungen verloren. Stellen Sie daher sicher, dass Sie Ihre Analyse in einer einzigen Sitzung abschließen oder ein kopierbares Skript einrichten, das Sie verwenden können, um Ihre Umgebung einzurichten.

Von diesem Punkt an sollten Sie

```sh
# apt update
```

(Hinweis: `sudo` ist nicht installiert, aber es ist auch nicht notwendig, da Sie als `root` arbeiten, sodass Sie `sudo` aus allen Befehlen weglassen können.)

Dann fügen Sie alle [build dependencies](#required-build-tools-and-external-libraries), einen Konsolen-basierten Editor Ihrer Wahl, `git` und alles andere, was Sie benötigen (z.B. `gdb`, `rr` usw.) hinzu. Wählen Sie ein Verzeichnis, in dem Sie arbeiten möchten, und `git clone` Julia, wechseln Sie zu dem Branch, den Sie debuggen möchten, und bauen Sie Julia wie gewohnt.

## Update the version number of a dependency

Es gibt zwei Arten von Builds.

1. Bauen Sie alles (`deps/` und `src/`) aus dem Quellcode. (Fügen Sie `USE_BINARYBUILDER=0` zu `Make.user` hinzu, siehe [Building Julia](#building-julia))
2. Aus dem Quellcode (`src/`) mit vorcompilierten Abhängigkeiten (Standard) bauen

Wenn Sie die Versionsnummer einer Abhängigkeit in `deps/` aktualisieren möchten, sollten Sie die folgende Checkliste verwenden:

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

Hinweis:

  * Für spezifische Abhängigkeiten sind einige Elemente in der Checkliste möglicherweise nicht vorhanden.
  * Für die Prüfzifferdatei kann es sich um **eine einzelne Datei** ohne Endung oder **einen Ordner** handeln, der zwei Dateien enthält.

### Example: `OpenLibm`

1. Aktualisieren Sie die Versionsnummern in `deps/openlibm.version`

      * `OPENLIBM_VER := 0.X.Y`
      * `OPENLIBM_BRANCH = v0.X.Y`
      * `OPENLIBM_SHA1 = neuer-sha1-hash`
2. Aktualisieren Sie die Versionsnummer in `stdlib/OpenLibm_jll/Project.toml`

      * `version = "0.X.Y+0"`
3. Aktualisieren Sie die Prüfziffern in `deps/checksums/openlibm`

      * `make -f contrib/refresh_checksums.mk openlibm`
4. Überprüfen Sie, ob die Patch-Dateien `deps/patches/openlibm-*.patch` existieren.

      * wenn Patches nicht existieren, überspringen.
      * Wenn Patches vorhanden sind, überprüfen Sie, ob sie in die neue Version integriert wurden und entfernt werden müssen. Beim Löschen eines Patches denken Sie daran, die entsprechende Makefile-Datei (`deps/openlibm.mk`) zu ändern.
