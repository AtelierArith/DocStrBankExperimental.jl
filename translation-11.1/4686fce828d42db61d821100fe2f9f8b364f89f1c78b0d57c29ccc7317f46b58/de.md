# Windows

Diese Datei beschreibt, wie man Julia unter Windows installiert, erstellt und verwendet.

Für allgemeinere Informationen über Julia siehe die [main README](https://github.com/JuliaLang/julia/blob/master/README.md) oder die [documentation](https://docs.julialang.org).

## General Information for Windows

Wir empfehlen dringend, Julia mit einer modernen Terminalanwendung auszuführen, insbesondere Windows Terminal, das von der [Microsoft Store](https://aka.ms/terminal) installiert werden kann.

### Line endings

Julia verwendet ausschließlich Binärdateien. Im Gegensatz zu vielen anderen Windows-Programmen erhalten Sie, wenn Sie `\n` in eine Datei schreiben, ein `\n` in der Datei und nicht ein anderes Bitmuster. Dies entspricht dem Verhalten anderer Betriebssysteme. Wenn Sie Git für Windows installiert haben, wird empfohlen, aber nicht zwingend erforderlich, dass Sie Ihr System-Git so konfigurieren, dass es dasselbe Konventionsmuster verwendet:

```sh
git config --global core.eol lf
git config --global core.autocrlf input
```

oder bearbeiten Sie `%USERPROFILE%\.gitconfig` und fügen Sie die Zeilen hinzu/bearbeiten Sie sie:

```
[core]
    eol = lf
    autocrlf = input
```

## Binary distribution

Für die Installationshinweise zur binären Verteilung unter Windows siehe die Anweisungen unter [https://julialang.org/downloads/platform/#windows](https://julialang.org/downloads/platform/#windows).

## Source distribution

### Cygwin-to-MinGW cross-compiling

Die empfohlene Methode zum Kompilieren von Julia aus dem Quellcode unter Windows besteht darin, von [Cygwin](https://www.cygwin.com) aus cross zu kompilieren, wobei Versionen der MinGW-w64-Compiler verwendet werden, die über den Paketmanager von Cygwin verfügbar sind.

1. Laden Sie das Cygwin-Setup für [32 bit](https://cygwin.com/setup-x86.exe) oder [64 bit](https://cygwin.com/setup-x86_64.exe) herunter und führen Sie es aus. Beachten Sie, dass Sie entweder 32-Bit- oder 64-Bit-Julia aus entweder 32-Bit- oder 64-Bit-Cygwin kompilieren können. 64-Bit-Cygwin hat eine etwas kleinere, aber oft aktuellere Auswahl an Paketen.

    *Fortgeschritten*: Sie können die Schritte 2-4 überspringen, indem Sie Folgendes ausführen:

    ```sh
    setup-x86_64.exe -s <url> -q -P cmake,gcc-g++,git,make,patch,curl,m4,python3,p7zip,mingw64-i686-gcc-g++,mingw64-i686-gcc-fortran,mingw64-x86_64-gcc-g++,mingw64-x86_64-gcc-fortran
    ```

    replacing `<url>` with a site from [https://cygwin.com/mirrors.html](https://cygwin.com/mirrors.html) or run setup manually first and select a mirror.
2. Wählen Sie den Installationsort und einen Spiegelserver zum Herunterladen aus.
3. Wählen Sie im Schritt *Pakete auswählen* Folgendes aus:

    1. Aus der Kategorie *Devel*: `cmake`, `gcc-g++`, `git`, `make`, `patch`
    2. Aus der Kategorie *Net*: `curl`
    3. Aus der Kategorie *Interpreters* (oder *Python*): `m4`, `python3`
    4. Aus der Kategorie *Archiv*: `p7zip`
    5. Für 32-Bit Julia und auch aus der *Devel*-Kategorie:  `mingw64-i686-gcc-g++` und `mingw64-i686-gcc-fortran`
    6. Für 64-Bit Julia und auch aus der *Devel*-Kategorie:  `mingw64-x86_64-gcc-g++` und `mingw64-x86_64-gcc-fortran`
4. Lassen Sie die Cygwin-Installation abschließen und starten Sie dann über die installierte Verknüpfung *'Cygwin Terminal'* oder *'Cygwin64 Terminal'*, je nach Bedarf.
5. Bauen Sie Julia und ihre Abhängigkeiten aus dem Quellcode:

    1. Holen Sie sich die Julia-Quellen

        ```sh
        git clone https://github.com/JuliaLang/julia.git
        cd julia
        ```

        Tipp: Wenn Sie einen `error: cannot fork() for fetch-pack: Resource temporarily unavailable` von git erhalten, fügen Sie `alias git="env PATH=/usr/bin git"` zu `~/.bashrc` hinzu und starten Sie Cygwin neu.
    2. Setze die `XC_HOST`-Variable in `Make.user`, um die MinGW-w64-Kreuzkompilierung anzugeben.

        ```sh
        echo 'XC_HOST = i686-w64-mingw32' > Make.user     # for 32 bit Julia
        # or
        echo 'XC_HOST = x86_64-w64-mingw32' > Make.user   # for 64 bit Julia
        ```
    3. Starten Sie den Build

        ```sh
        make -j 4       # Adjust the number of threads (4) to match your build environment.
        make -j 4 debug # This builds julia-debug.exe
        ```
6. Führen Sie Julia direkt über die Julia-Executables aus

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

[MSYS2](https://www.msys2.org/) ist eine Softwareverteilung und Build-Umgebung für Windows.

Hinweis: MSYS2 erfordert **64-Bit** Windows 7 oder neuer.

1. Installieren und konfigurieren Sie MSYS2.

    1. Laden Sie den neuesten Installer für die [64-bit](https://github.com/msys2/msys2-installer/releases/latest) Distribution herunter und führen Sie ihn aus. Der Installer wird einen Namen wie `msys2-x86_64-yyyymmdd.exe` haben.
    2. Öffnen Sie die MSYS2-Shell. Aktualisieren Sie die Paketdatenbank und die Basis-Pakete:

        `pacman -Syu`
    3. Beenden Sie MSYS2 und starten Sie es neu. Aktualisieren Sie den Rest der Basis-Pakete:

        `pacman -Syu`
    4. Dann installieren Sie die erforderlichen Werkzeuge zum Erstellen von Julia:

        `pacman -S cmake diffutils git m4 make patch tar p7zip curl python`

        Für 64-Bit Julia installieren Sie die x86_64-Version:

        `pacman -S mingw-w64-x86_64-gcc`

        Für 32-Bit Julia, installieren Sie die i686-Version:

        `pacman -S mingw-w64-i686-gcc`
    5. Die Konfiguration von MSYS2 ist abgeschlossen. Jetzt `exit` die MSYS2-Shell.
2. Bauen Sie Julia und ihre Abhängigkeiten mit vorgefertigten Abhängigkeiten.

    1. Öffnen Sie ein neues [**MINGW64/MINGW32 shell**](https://www.msys2.org/docs/environments/#overview). Derzeit können wir sowohl mingw32 als auch mingw64 nicht verwenden, daher müssen Sie, wenn Sie die x86_64- und i686-Versionen erstellen möchten, diese in jeder Umgebung separat erstellen.
    2. Klonen Sie die Julia-Quellen:

        `git clone https://github.com/JuliaLang/julia.git  cd julia`
    3. Starten Sie den Build

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

Sie können auch MinGW-w64-Cross-Compiler verwenden, um eine Windows-Version von Julia von Linux, Mac oder dem Windows-Subsystem für Linux (WSL) zu erstellen.

Zuerst müssen Sie sicherstellen, dass Ihr System die erforderlichen Abhängigkeiten hat. Wir benötigen Wine (>=1.7.5), einen Systemcompiler und einige Downloader. Hinweis: Eine Cygwin-Installation könnte diese Methode stören, wenn WSL verwendet wird.

**Auf Ubuntu** (auf anderen Linux-Systemen sind die Abhängigkeitsnamen wahrscheinlich ähnlich):

```sh
apt-get install wine-stable gcc wget p7zip-full winbind mingw-w64 gfortran-mingw-w64
dpkg --add-architecture i386 && apt-get update && apt-get install wine32 # add sudo to each if needed
# switch all of the following to their "-posix" variants (interactively):
for pkg in i686-w64-mingw32-g++ i686-w64-mingw32-gcc i686-w64-mingw32-gfortran x86_64-w64-mingw32-g++ x86_64-w64-mingw32-gcc x86_64-w64-mingw32-gfortran; do
    sudo update-alternatives --config $pkg
done
```

**Auf Mac**: Installieren Sie XCode, die XCode-Befehlszeilentools, X11 (jetzt [XQuartz](https://www.xquartz.org/)) und [MacPorts](https://www.macports.org/install.php) oder [Homebrew](https://brew.sh/). Führen Sie dann `port install wine wget mingw-w64` oder `brew install wine wget mingw-w64` aus, je nach Bedarf.

**Dann führen Sie den Build aus:**

1. `git clone https://github.com/JuliaLang/julia.git julia-win32`
2. `cd julia-win32`
3. `echo override XC_HOST = i686-w64-mingw32 >> Make.user`
4. `machen`
5. `make win-extras` (Notwendig, bevor `make binary-dist` ausgeführt wird)
6. `make binary-dist` dann `make exe`, um das Windows-Installationsprogramm zu erstellen.
7. verschiebe den `julia-*.exe` Installer auf die Zielmaschine

Wenn Sie für 64-Bit-Windows erstellen, sind die Schritte im Wesentlichen die gleichen. Ersetzen Sie einfach `i686` in `XC_HOST` durch `x86_64`. (Hinweis: Auf Mac läuft Wine nur im 32-Bit-Modus).

## Debugging a cross-compiled build under wine

Der effektivste Weg, eine cross-kompilierte Version von Julia auf dem Cross-Kompilierungs-Host zu debuggen, besteht darin, eine Windows-Version von GDB zu installieren und sie wie gewohnt unter Wine auszuführen. Die verfügbaren vorgefertigten Pakete [as part of the MSYS2 project](https://packages.msys2.org/) sind bekannt dafür, dass sie funktionieren. Neben dem GDB-Paket benötigen Sie möglicherweise auch die Python- und Termcap-Pakete. Schließlich funktioniert die Eingabeaufforderung von GDB möglicherweise nicht, wenn sie von der Befehlszeile aus gestartet wird. Dies kann umgangen werden, indem `wineconsole` vor dem regulären GDB-Befehl hinzugefügt wird.

## After compiling

Das Kompilieren mit einer der oben genannten Optionen erstellt eine grundlegende Julia-Build, jedoch nicht einige zusätzliche Komponenten, die enthalten sind, wenn Sie den vollständigen Julia-Binary-Installer ausführen. Wenn Sie diese Komponenten benötigen, ist der einfachste Weg, sie zu erhalten, den Installer selbst zu erstellen, indem Sie `make win-extras` gefolgt von `make binary-dist` und `make exe` ausführen. Führen Sie dann den resultierenden Installer aus.

## Windows Build Debugging

### GDB hangs with Cygwin mintty

  * Führen Sie GDB stattdessen unter der Windows-Konsole (cmd) aus. GDB [may not function properly](https://www.cygwin.com/ml/cygwin/2009-02/msg00531.html) unter mintty mit Nicht-Cygwin-Anwendungen. Sie können `cmd /c start` verwenden, um die Windows-Konsole von mintty aus zu starten, falls erforderlich.

### GDB not attaching to the right process

  * Verwenden Sie die PID aus dem Windows-Task-Manager oder `WINPID` aus dem `ps`-Befehl anstelle der PID aus Unix-ähnlichen Befehlszeilenwerkzeugen (z. B. `pgrep`). Möglicherweise müssen Sie die PID-Spalte hinzufügen, wenn sie standardmäßig nicht im Windows-Task-Manager angezeigt wird.

### GDB not showing the right backtrace

  * Beim Anfügen an den Julia-Prozess könnte GDB nicht an den richtigen Thread angehängt werden. Verwenden Sie den Befehl `info threads`, um alle Threads anzuzeigen, und `thread <threadno>`, um die Threads zu wechseln.
  * Stellen Sie sicher, dass Sie eine 32-Bit-Version von GDB verwenden, um eine 32-Bit-Build von Julia zu debuggen, oder eine 64-Bit-Version von GDB, um eine 64-Bit-Build von Julia zu debuggen.

### Build process is slow/eats memory/hangs my computer

  * Disable the Windows [Superfetch](https://en.wikipedia.org/wiki/Windows_Vista_I/O_technologies#SuperFetch) and [Program Compatibility Assistant](https://blogs.msdn.com/b/cjacks/archive/2011/11/22/managing-the-windows-7-program-compatibility-assistant-pca.aspx) services, as they are known to have [spurious interactions](https://cygwin.com/ml/cygwin/2011-12/msg00058.html) with MinGW/Cygwin.

    Wie im obigen Link erwähnt: Übermäßiger Speicherverbrauch durch `svchost` kann im Task-Manager untersucht werden, indem auf den speicherintensiven `svchost.exe`-Prozess geklickt und `Zu Diensten wechseln` ausgewählt wird. Deaktivieren Sie die untergeordneten Dienste nacheinander, bis der Übeltäter gefunden ist.
  * Achten Sie auf [BLODA](https://cygwin.com/faq/faq.html#faq.using.bloda). Das [vmmap](https://technet.microsoft.com/en-us/sysinternals/dd535533.aspx) Werkzeug ist unverzichtbar, um solche Softwarekonflikte zu identifizieren. Verwenden Sie vmmap, um die Liste der geladenen DLLs für bash, mintty oder einen anderen persistenten Prozess, der zum Erstellen verwendet wird, zu überprüfen. Im Wesentlichen ist *jede* DLL außerhalb des Windows-Systemverzeichnisses potenzielles BLODA.
