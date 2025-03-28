# Environment Variables

Julia kann mit einer Reihe von Umgebungsvariablen konfiguriert werden, die entweder auf die übliche Weise für jedes Betriebssystem oder auf eine tragbare Weise innerhalb von Julia festgelegt werden. Angenommen, Sie möchten die Umgebungsvariable [`JULIA_EDITOR`](@ref JULIA_EDITOR) auf `vim` setzen, können Sie `ENV["JULIA_EDITOR"] = "vim"` eingeben (zum Beispiel im REPL), um diese Änderung fallweise vorzunehmen, oder dasselbe in die Benutzerkonfigurationsdatei `~/.julia/config/startup.jl` im Home-Verzeichnis des Benutzers hinzufügen, um eine dauerhafte Wirkung zu erzielen. Der aktuelle Wert derselben Umgebungsvariable kann durch die Auswertung von `ENV["JULIA_EDITOR"]` bestimmt werden.

Die Umgebungsvariablen, die Julia verwendet, beginnen im Allgemeinen mit `JULIA`. Wenn [`InteractiveUtils.versioninfo`](@ref) mit dem Schlüsselwort `verbose=true` aufgerufen wird, listet die Ausgabe alle definierten Umgebungsvariablen auf, die für Julia relevant sind, einschließlich derjenigen, die `JULIA` in ihren Namen enthalten.

!!! note
    Es wird empfohlen, während der Laufzeit keine Umgebungsvariablen zu ändern, wie zum Beispiel in einer `~/.julia/config/startup.jl`.

    Ein Grund dafür ist, dass einige Julia-Variablen, wie [`JULIA_NUM_THREADS`](@ref JULIA_NUM_THREADS) und [`JULIA_PROJECT`](@ref JULIA_PROJECT), vor dem Start von Julia gesetzt werden müssen.

    Ähnlich werden die `__init__()`-Funktionen von Benutzermodulen im sysimage (über PackageCompiler) vor `startup.jl` ausgeführt, sodass das Setzen von Umgebungsvariablen in einer `startup.jl` möglicherweise zu spät für Benutzercode ist.

    Darüber hinaus kann das Ändern von Umgebungsvariablen zur Laufzeit Datenrennen in ansonsten harmlosen Code einführen.

    In Bash können Umgebungsvariablen entweder manuell gesetzt werden, indem man z. B. `export JULIA_NUM_THREADS=4` vor dem Start von Julia ausführt, oder indem man denselben Befehl zu `~/.bashrc` oder `~/.bash_profile` hinzufügt, um die Variable jedes Mal zu setzen, wenn Bash gestartet wird.


## File locations

### [`JULIA_BINDIR`](@id JULIA_BINDIR)

Der absolute Pfad des Verzeichnisses, das die Julia-Ausführungsdatei enthält, setzt die globale Variable [`Sys.BINDIR`](@ref). Wenn `$JULIA_BINDIR` nicht gesetzt ist, bestimmt Julia den Wert `Sys.BINDIR` zur Laufzeit.

Die ausführbare Datei selbst ist eine von

```
$JULIA_BINDIR/julia
$JULIA_BINDIR/julia-debug
```

standardmäßig.

Die globale Variable `Base.DATAROOTDIR` bestimmt einen relativen Pfad von `Sys.BINDIR` zum Datenverzeichnis, das mit Julia verbunden ist. Dann der Pfad

```
$JULIA_BINDIR/$DATAROOTDIR/julia/base
```

bestimmt das Verzeichnis, in dem Julia zunächst nach Quelldateien sucht (über `Base.find_source_file()`).

Ebenso bestimmt die globale Variable `Base.SYSCONFDIR` einen relativen Pfad zum Verzeichnis der Konfigurationsdateien. Dann sucht Julia nach einer `startup.jl`-Datei in

```
$JULIA_BINDIR/$SYSCONFDIR/julia/startup.jl
$JULIA_BINDIR/../etc/julia/startup.jl
```

standardmäßig (über `Base.load_julia_startup()`).

Zum Beispiel hat eine Linux-Installation mit einer Julia-Ausführungsdatei, die sich unter `/bin/julia` befindet, einem `DATAROOTDIR` von `../share` und einem `SYSCONFDIR` von `../etc`, [`JULIA_BINDIR`](@ref JULIA_BINDIR) auf `/bin` gesetzt, einen Suchpfad für Quell-Dateien von

```
/share/julia/base
```

und einen globalen Konfigurationssuchpfad von

```
/etc/julia/startup.jl
```

### [`JULIA_PROJECT`](@id JULIA_PROJECT)

Ein Verzeichnispfad, der angibt, welches Projekt das anfängliche aktive Projekt sein sollte. Das Setzen dieser Umgebungsvariable hat denselben Effekt wie die Angabe der `--project` Startoption, aber `--project` hat eine höhere Priorität. Wenn die Variable auf `@.` gesetzt ist (beachten Sie den nachgestellten Punkt), versucht Julia, ein Projektverzeichnis zu finden, das eine `Project.toml` oder `JuliaProject.toml` Datei aus dem aktuellen Verzeichnis und dessen übergeordneten Verzeichnissen enthält. Siehe auch das Kapitel über [Code Loading](@ref code-loading).

!!! note
    [`JULIA_PROJECT`](@ref JULIA_PROJECT) muss definiert werden, bevor Julia gestartet wird; es ist zu spät im Startprozess, es in `startup.jl` zu definieren.


### [`JULIA_LOAD_PATH`](@id JULIA_LOAD_PATH)

Die [`JULIA_LOAD_PATH`](@ref JULIA_LOAD_PATH) Umgebungsvariable wird verwendet, um die globale Julia [`LOAD_PATH`](@ref) Variable zu befüllen, die bestimmt, welche Pakete über `import` und `using` geladen werden können (siehe [Code Loading](@ref code-loading)).

Im Gegensatz zur Shell-Variable `PATH` werden leere Einträge in [`JULIA_LOAD_PATH`](@ref JULIA_LOAD_PATH) beim Befüllen von `LOAD_PATH` auf den Standardwert `LOAD_PATH`, `["@", "@v#.#", "@stdlib"]`, erweitert. Dies ermöglicht ein einfaches Anhängen, Voranstellen usw. des Ladepfadwerts in Shell-Skripten, unabhängig davon, ob `4d61726b646f776e2e436f64652822222c20224a554c49415f4c4f41445f504154482229_40726566204a554c49415f4c4f41445f50415448` bereits gesetzt ist oder nicht. Um beispielsweise das Verzeichnis `/foo/bar` an `LOAD_PATH` voranzustellen, tun Sie einfach

```sh
export JULIA_LOAD_PATH="/foo/bar:$JULIA_LOAD_PATH"
```

Wenn die Umgebungsvariable [`JULIA_LOAD_PATH`](@ref JULIA_LOAD_PATH) bereits gesetzt ist, wird ihr alter Wert mit `/foo/bar` vorangestellt. Andernfalls, wenn `4d61726b646f776e2e436f64652822222c20224a554c49415f4c4f41445f504154482229_40726566204a554c49415f4c4f41445f50415448` nicht gesetzt ist, wird sie auf `/foo/bar:` gesetzt, was zu einem `LOAD_PATH`-Wert von `["/foo/bar", "@", "@v#.#", "@stdlib"]` expandiert. Wenn `4d61726b646f776e2e436f64652822222c20224a554c49415f4c4f41445f504154482229_40726566204a554c49415f4c4f41445f50415448` auf den leeren String gesetzt ist, expandiert es zu einem leeren `LOAD_PATH`-Array. Mit anderen Worten, der leere String wird als ein Array mit null Elementen interpretiert, nicht als ein Array mit einem Element des leeren Strings. Dieses Verhalten wurde gewählt, um es zu ermöglichen, einen leeren Ladepfad über die Umgebungsvariable zu setzen. Wenn Sie den Standardladepfad möchten, setzen Sie entweder die Umgebungsvariable zurück oder, falls sie einen Wert haben muss, setzen Sie sie auf den String `:`.

!!! note
    Auf Windows werden Pfadelemente durch das `;`-Zeichen getrennt, wie es bei den meisten Pfadlisten unter Windows der Fall ist. Ersetzen Sie `:` durch `;` im obigen Absatz.


### [`JULIA_DEPOT_PATH`](@id JULIA_DEPOT_PATH)

Die [`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH) Umgebungsvariable wird verwendet, um die globale Julia [`DEPOT_PATH`](@ref) Variable zu befüllen, die steuert, wo der Paketmanager sowie Julias Code-Lade-Mechanismen nach Paketregistrierungen, installierten Paketen, benannten Umgebungen, Repo-Kopien, zwischengespeicherten kompilierten Paketbildern, Konfigurationsdateien und dem Standardstandort der REPL-Historie-Datei suchen.

Im Gegensatz zur Shell-Variable `PATH`, aber ähnlich zu [`JULIA_LOAD_PATH`](@ref JULIA_LOAD_PATH), haben leere Einträge in [`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH) ein spezielles Verhalten:

  * Am Ende wird es auf den Standardwert von `DEPOT_PATH` erweitert, *ausgenommen* das Benutzerdepot.
  * Zu Beginn wird es auf den Standardwert von `DEPOT_PATH` *einschließlich* des Benutzerdepots erweitert.

Dies ermöglicht eine einfache Überschreibung des Benutzerdepots, während der Zugriff auf Ressourcen, die mit Julia gebündelt sind, wie Cache-Dateien, Artefakte usw., erhalten bleibt. Um beispielsweise das Benutzerdepot auf `/foo/bar` zu wechseln, verwenden Sie ein abschließendes `:`.

```sh
export JULIA_DEPOT_PATH="/foo/bar:"
```

Alle Paketoperationen, wie das Klonen von Registrierungen oder das Installieren von Paketen, schreiben jetzt in `/foo/bar`. Da der leere Eintrag jedoch auf das Standard-Systemdepot erweitert wird, sind alle gebündelten Ressourcen weiterhin verfügbar. Wenn Sie wirklich nur das Depot unter `/foo/bar` verwenden möchten und keine gebündelten Ressourcen laden möchten, setzen Sie einfach die Umgebungsvariable auf `/foo/bar` ohne den abschließenden Doppelpunkt.

Um ein Depot am Ende der vollständigen Standardliste hinzuzufügen, einschließlich des Standardbenutzerdepots, verwenden Sie ein führendes `:`

```sh
export JULIA_DEPOT_PATH=":/foo/bar"
```

Es gibt zwei Ausnahmen von der oben genannten Regel. Erstens, wenn [`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH) auf den leeren String gesetzt wird, erweitert es sich zu einem leeren `DEPOT_PATH` Array. Mit anderen Worten, der leere String wird als ein Array mit null Elementen interpretiert, nicht als ein Array mit einem Element des leeren Strings. Dieses Verhalten wurde gewählt, um es zu ermöglichen, einen leeren Depot-Pfad über die Umgebungsvariable festzulegen.

Zweitens, wenn kein Benutzerdepot in [`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH) angegeben ist, wird der leere Eintrag auf das Standarddepot *einschließlich* des Benutzerdepots erweitert. Dies ermöglicht es, das Standarddepot zu verwenden, als ob die Umgebungsvariable nicht gesetzt wäre, indem sie auf den String `:` gesetzt wird.

!!! note
    Auf Windows werden Pfadelemente durch das `;`-Zeichen getrennt, wie es bei den meisten Pfadlisten unter Windows der Fall ist. Ersetzen Sie `:` durch `;` im obigen Absatz.


!!! note
    [`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH) muss definiert werden, bevor Julia gestartet wird; es ist zu spät im Startprozess, dies in `startup.jl` zu definieren; zu diesem Zeitpunkt können Sie stattdessen direkt das `DEPOT_PATH`-Array ändern, das aus der Umgebungsvariable befüllt wird.


### [`JULIA_HISTORY`](@id JULIA_HISTORY)

Der absolute Pfad `REPL.find_hist_file()` der Verlaufdatei des REPL. Wenn `$JULIA_HISTORY` nicht gesetzt ist, dann wird `REPL.find_hist_file()` standardmäßig auf

```
$(DEPOT_PATH[1])/logs/repl_history.jl
```

### [`JULIA_MAX_NUM_PRECOMPILE_FILES`](@id JULIA_MAX_NUM_PRECOMPILE_FILES)

Legt die maximale Anzahl verschiedener Instanzen eines einzelnen Pakets fest, die im Precompile-Cache gespeichert werden sollen (Standard = 10).

### [`JULIA_VERBOSE_LINKING`](@id JULIA_VERBOSE_LINKING)

Wenn auf true gesetzt, werden Linker-Befehle während der Vorcompilierung angezeigt.

## Pkg.jl

### [`JULIA_CI`](@id JULIA_CI)

Wenn auf `true` gesetzt, zeigt dies dem Paketserver an, dass alle Paketoperationen Teil eines Continuous Integration (CI) Systems sind, um Paketnutzungsstatistiken zu sammeln.

### [`JULIA_NUM_PRECOMPILE_TASKS`](@id JULIA_NUM_PRECOMPILE_TASKS)

Die Anzahl der parallelen Aufgaben, die beim Vorcompilieren von Paketen verwendet werden sollen. Siehe [`Pkg.precompile`](https://pkgdocs.julialang.org/v1/api/#Pkg.precompile).

### [`JULIA_PKG_DEVDIR`](@id JULIA_PKG_DEVDIR)

Das Standardverzeichnis, das von [`Pkg.develop`](https://pkgdocs.julialang.org/v1/api/#Pkg.develop) zum Herunterladen von Paketen verwendet wird.

### [`JULIA_PKG_IGNORE_HASHES`](@id JULIA_PKG_IGNORE_HASHES)

Wenn auf `1` gesetzt, ignoriert dies falsche Hashes in Artefakten. Dies sollte mit Vorsicht verwendet werden, da es die Überprüfung von Downloads deaktiviert, aber Probleme beim Verschieben von Dateien zwischen verschiedenen Dateisystemtypen lösen kann. Siehe [Pkg.jl issue #2317](https://github.com/JuliaLang/Pkg.jl/issues/2317) für weitere Details.

!!! compat "Julia 1.6"
    Dies wird nur in Julia 1.6 und höher unterstützt.


### [`JULIA_PKG_OFFLINE`](@id JULIA_PKG_OFFLINE)

Wenn auf `true` gesetzt, wird der Offline-Modus aktiviert: siehe [`Pkg.offline`](https://pkgdocs.julialang.org/v1/api/#Pkg.offline).

!!! compat "Julia 1.5"
    Pkg's Offline-Modus erfordert Julia 1.5 oder später.


### [`JULIA_PKG_PRECOMPILE_AUTO`](@id JULIA_PKG_PRECOMPILE_AUTO)

Wenn auf `0` gesetzt, wird die automatische Vorcompilierung durch Paketaktionen, die das Manifest ändern, deaktiviert. Siehe [`Pkg.precompile`](https://pkgdocs.julialang.org/v1/api/#Pkg.precompile).

### [`JULIA_PKG_SERVER`](@id JULIA_PKG_SERVER)

Gibt die URL des zu verwendenden Paket-Registrierungsdienstes an. Standardmäßig verwendet `Pkg` `https://pkg.julialang.org`, um Julia-Pakete abzurufen. Darüber hinaus können Sie die Verwendung des PkgServer-Protokolls deaktivieren und stattdessen direkt von ihren Hosts (GitHub, GitLab usw.) auf die Pakete zugreifen, indem Sie festlegen: `export JULIA_PKG_SERVER=""`

### [`JULIA_PKG_SERVER_REGISTRY_PREFERENCE`](@id JULIA_PKG_SERVER_REGISTRY_PREFERENCE)

Gibt den bevorzugten Registrierungsstil an. Derzeit unterstützte Werte sind `conservative` (der Standard), der nur Ressourcen veröffentlicht, die vom Speicherserver verarbeitet wurden (und daher eine höhere Wahrscheinlichkeit haben, von den PkgServers verfügbar zu sein), während `eager` Registrierungen veröffentlicht, deren Ressourcen möglicherweise nicht unbedingt von den Speicherservern verarbeitet wurden. Benutzer hinter restriktiven Firewalls, die das Herunterladen von beliebigen Servern nicht zulassen, sollten den `eager` Stil nicht verwenden.

!!! compat "Julia 1.7"
    Dies betrifft nur Julia 1.7 und höher.


### [`JULIA_PKG_UNPACK_REGISTRY`](@id JULIA_PKG_UNPACK_REGISTRY)

Wenn auf `true` gesetzt, wird das Registry entpackt, anstatt es als komprimiertes Tarball zu speichern.

!!! compat "Julia 1.7"
    Dies betrifft nur Julia 1.7 und höher. Frühere Versionen entpacken das Register immer.


### [`JULIA_PKG_USE_CLI_GIT`](@id JULIA_PKG_USE_CLI_GIT)

Wenn auf `true` gesetzt, verwenden Pkg-Operationen, die das Git-Protokoll nutzen, ein externes `git`-Executable anstelle der standardmäßigen libgit2-Bibliothek.

!!! compat "Julia 1.7"
    Die Verwendung des `git`-Executables wird nur für Julia 1.7 und höher unterstützt.


### [`JULIA_PKGRESOLVE_ACCURACY`](@id JULIA_PKGRESOLVE_ACCURACY)

Die Genauigkeit des Paketauflösers. Dies sollte eine positive ganze Zahl sein, der Standardwert ist `1`.

### [`JULIA_PKG_PRESERVE_TIERED_INSTALLED`](@id JULIA_PKG_PRESERVE_TIERED_INSTALLED)

Ändern Sie die Standardstrategie für die Paketinstallation in `Pkg.PRESERVE_TIERED_INSTALLED`, um dem Paketmanager zu ermöglichen, Versionen von Paketen zu installieren, während so viele Versionen von bereits installierten Paketen wie möglich beibehalten werden.

!!! compat "Julia 1.9"
    Dies betrifft nur Julia 1.9 und höher.


## Network transport

### [`JULIA_NO_VERIFY_HOSTS`](@id JULIA_NO_VERIFY_HOSTS)

### [`JULIA_SSL_NO_VERIFY_HOSTS`](@id JULIA_SSL_NO_VERIFY_HOSTS)

### [`JULIA_SSH_NO_VERIFY_HOSTS`](@id JULIA_SSH_NO_VERIFY_HOSTS)

### [`JULIA_ALWAYS_VERIFY_HOSTS`](@id JULIA_ALWAYS_VERIFY_HOSTS)

Spezifizieren Sie Hosts, deren Identität für bestimmte Transportprotokolle überprüft werden soll oder nicht. Siehe [`NetworkOptions.verify_host`](https://github.com/JuliaLang/NetworkOptions.jl#verify_host)

### [`JULIA_SSL_CA_ROOTS_PATH`](@id JULIA_SSL_CA_ROOTS_PATH)

Geben Sie die Datei oder das Verzeichnis an, das die Wurzeln der Zertifizierungsstelle enthält. Siehe [`NetworkOptions.ca_roots`](https://github.com/JuliaLang/NetworkOptions.jl#ca_roots)

## External applications

### [`JULIA_SHELL`](@id JULIA_SHELL)

Der absolute Pfad der Shell, mit der Julia externe Befehle ausführen sollte (über `Base.repl_cmd()`). Standardmäßig wird die Umgebungsvariable `$SHELL` verwendet, und es wird auf `/bin/sh` zurückgegriffen, wenn `$SHELL` nicht gesetzt ist.

!!! note
    Unter Windows wird diese Umgebungsvariable ignoriert, und externe Befehle werden direkt ausgeführt.


### [`JULIA_EDITOR`](@id JULIA_EDITOR)

Der von `InteractiveUtils.editor()` zurückgegebene Editor, der z.B. in [`InteractiveUtils.edit`](@ref) verwendet wird, bezieht sich auf den Befehl des bevorzugten Editors, zum Beispiel `vim`.

`$JULIA_EDITOR` hat Vorrang vor `$VISUAL`, das wiederum Vorrang vor `$EDITOR` hat. Wenn keine dieser Umgebungsvariablen gesetzt ist, wird der Editor unter Windows und OS X als `open` betrachtet, oder `/etc/alternatives/editor`, falls es existiert, oder `emacs` andernfalls.

Um Visual Studio Code unter Windows zu verwenden, setzen Sie `$JULIA_EDITOR` auf `code.cmd`.

## Parallelization

### [`JULIA_CPU_THREADS`](@id JULIA_CPU_THREADS)

Überschreibt die globale Variable [`Base.Sys.CPU_THREADS`](@ref), die Anzahl der verfügbaren logischen CPU-Kerne.

### [`JULIA_WORKER_TIMEOUT`](@id JULIA_WORKER_TIMEOUT)

Ein [`Float64`](@ref), der den Wert von `Distributed.worker_timeout()` festlegt (Standard: `60.0`). Diese Funktion gibt die Anzahl der Sekunden an, die ein Arbeitsprozess warten wird, bis ein Masterprozess eine Verbindung herstellt, bevor er beendet wird.

### [`JULIA_NUM_THREADS`](@id JULIA_NUM_THREADS)

Eine nicht signierte 64-Bit-Ganzzahl (`uint64_t`), die die maximale Anzahl von Threads festlegt, die Julia zur Verfügung stehen. Wenn `$JULIA_NUM_THREADS` nicht positiv ist oder nicht gesetzt ist, oder wenn die Anzahl der CPU-Threads nicht durch Systemaufrufe bestimmt werden kann, wird die Anzahl der Threads auf `1` gesetzt.

Wenn `$JULIA_NUM_THREADS` auf `auto` gesetzt ist, wird die Anzahl der Threads auf die Anzahl der CPU-Threads gesetzt.

!!! note
    `JULIA_NUM_THREADS` muss vor dem Start von Julia definiert werden; es ist zu spät im Startprozess, um es in `startup.jl` zu definieren.


!!! compat "Julia 1.5"
    In Julia 1.5 und höher kann die Anzahl der Threads auch beim Start über das Kommandozeilenargument `-t`/`--threads` angegeben werden.


!!! compat "Julia 1.7"
    Der `auto`-Wert für `$JULIA_NUM_THREADS` erfordert Julia 1.7 oder höher.


### [`JULIA_THREAD_SLEEP_THRESHOLD`](@id JULIA_THREAD_SLEEP_THRESHOLD)

Wenn auf einen String gesetzt, der mit dem nicht groß-/kleinschreibungssensitiven Teilstring `"infinite"` beginnt, schlafen die drehenden Threads niemals. Andernfalls wird `$JULIA_THREAD_SLEEP_THRESHOLD` als unsigned 64-Bit-Ganzzahl (`uint64_t`) interpretiert und gibt in Nanosekunden die Zeit an, nach der drehende Threads schlafen sollten.

### [`JULIA_NUM_GC_THREADS`](@id JULIA_NUM_GC_THREADS)

Legt die Anzahl der Threads fest, die von der Garbage Collection verwendet werden. Wenn nicht angegeben, wird sie auf die Hälfte der Anzahl der Arbeits-Threads gesetzt.

!!! compat "Julia 1.10"
    Die Umgebungsvariable wurde in 1.10 hinzugefügt.


### [`JULIA_IMAGE_THREADS`](@id JULIA_IMAGE_THREADS)

Eine nicht signierte 32-Bit-Ganzzahl, die die Anzahl der Threads festlegt, die bei der Bildkompilierung in diesem Julia-Prozess verwendet werden. Der Wert dieser Variablen kann ignoriert werden, wenn das Modul ein kleines Modul ist. Wenn nicht angegeben, wird der kleinere Wert von [`JULIA_CPU_THREADS`](@ref JULIA_CPU_THREADS) oder der Hälfte der Anzahl der logischen CPU-Kerne an seiner Stelle verwendet.

### [`JULIA_IMAGE_TIMINGS`](@id JULIA_IMAGE_TIMINGS)

Ein boolescher Wert, der bestimmt, ob detaillierte Zeitinformationen während der Bildkompilierung ausgegeben werden. Standardmäßig auf 0.

### [`JULIA_EXCLUSIVE`](@id JULIA_EXCLUSIVE)

Wenn auf etwas anderes als `0` gesetzt, dann ist Julias Thread-Politik konsistent mit dem Betrieb auf einer dedizierten Maschine: Der Master-Thread läuft auf Prozessor 0, und die Threads sind affiniert. Andernfalls überlässt Julia dem Betriebssystem die Handhabung der Thread-Politik.

## REPL formatting

Umgebungsvariablen, die bestimmen, wie die REPL-Ausgabe im Terminal formatiert werden soll. Im Allgemeinen sollten diese Variablen auf [ANSI terminal escape sequences](https://en.wikipedia.org/wiki/ANSI_escape_code) gesetzt werden. Julia bietet eine hochgradige Schnittstelle mit vielen der gleichen Funktionen; siehe den Abschnitt über [The Julia REPL](@ref).

### [`JULIA_ERROR_COLOR`](@id JULIA_ERROR_COLOR)

Die Formatierung `Base.error_color()` (Standard: hellrot, `"\033[91m"`), die Fehler im Terminal haben sollten.

### [`JULIA_WARN_COLOR`](@id JULIA_WARN_COLOR)

Die Formatierung `Base.warn_color()` (Standard: gelb, `"\033[93m"`), die Warnungen im Terminal haben sollten.

### [`JULIA_INFO_COLOR`](@id JULIA_INFO_COLOR)

Die Formatierung `Base.info_color()` (Standard: cyan, `"\033[36m"`), die Informationen im Terminal haben sollten.

### [`JULIA_INPUT_COLOR`](@id JULIA_INPUT_COLOR)

Die Formatierung `Base.input_color()` (Standard: normal, `"\033[0m"`), die die Eingabe im Terminal haben sollte.

### [`JULIA_ANSWER_COLOR`](@id JULIA_ANSWER_COLOR)

Die Formatierung `Base.answer_color()` (Standard: normal, `"\033[0m"`), die die Ausgabe im Terminal haben sollte.

## System and Package Image Building

### [`JULIA_CPU_TARGET`](@id JULIA_CPU_TARGET)

Ändern Sie die Zielmaschinenarchitektur für (Vor-)Kompilierung [system](@ref sysimg-multi-versioning) und [package images](@ref pkgimgs-multi-versioning). `JULIA_CPU_TARGET` beeinflusst nur die Generierung von Maschinencode-Bildern, die in einem Festplattenspeicher ausgegeben werden. Im Gegensatz zu `--cpu-target` oder `-C`, [command line option](@ref cli), hat es keinen Einfluss auf die Just-in-Time (JIT) Code-Generierung innerhalb einer Julia-Sitzung, wo Maschinencode nur im Speicher gespeichert wird.

Gültige Werte für [`JULIA_CPU_TARGET`](@ref JULIA_CPU_TARGET) können durch Ausführen von `julia -C help` erhalten werden.

Das Setzen von [`JULIA_CPU_TARGET`](@ref JULIA_CPU_TARGET) ist wichtig für heterogene Rechensysteme, in denen Prozessoren unterschiedlicher Typen oder Merkmale vorhanden sein können. Dies wird häufig in Hochleistungsrechenclustern (HPC) festgestellt, da die Komponenten-Knoten unterschiedliche Prozessoren verwenden können.

Der CPU-Zielstring ist eine Liste von Strings, die durch `;` getrennt sind. Jeder String beginnt mit einem CPU- oder Architektur-Namen und wird gefolgt von einer optionalen Liste von Funktionen, die durch `,` getrennt sind. Ein `generic` oder leerer CPU-Name bedeutet das grundlegende erforderliche Funktionsset der Ziel-ISA, das mindestens der Architektur entspricht, mit der die C/C++-Laufzeit kompiliert wurde. Jeder String wird von LLVM interpretiert.

Einige spezielle Funktionen werden unterstützt:

1. `clone_all`

    Dies zwingt das Ziel, alle Funktionen in sysimg zu klonen. Wenn es in negativer Form verwendet wird (d.h. `-clone_all`), wird das standardmäßig für bestimmte Ziele aktivierte vollständige Klonen deaktiviert.
2. `basis([0-9]*)`

    Dies gibt den (0-basierten) Basiszielindex an. Das Basisziel ist das Ziel, auf dem das aktuelle Ziel basiert, d.h. die Funktionen, die nicht geklont werden, verwenden die Version im Basisziel. Diese Option bewirkt, dass das Basisziel vollständig geklont wird (als ob `clone_all` dafür angegeben ist), wenn es nicht das Standardziel (0) ist. Der Index kann nur kleiner als der aktuelle Index sein.
3. `opt_size`

    Optimieren Sie für die Größe mit minimalen Leistungseinbußen. Clang/GCCs `-Os`.
4. `min_size`

    Optimieren Sie nur für die Größe. Clangs `-Oz`.

## Debugging and profiling

### [`JULIA_DEBUG`](@id JULIA_DEBUG)

Aktivieren Sie das Debug-Protokoll für eine Datei oder ein Modul, siehe [`Logging`](@ref man-logging) für weitere Informationen.

### [`JULIA_PROFILE_PEEK_HEAP_SNAPSHOT`](@id JULIA_PROFILE_PEEK_HEAP_SNAPSHOT)

Aktivieren Sie das Sammeln eines Heap-Snapshots während der Ausführung über den Profiling-Peek-Mechanismus. Siehe [Triggered During Execution](@ref).

### [`JULIA_TIMING_SUBSYSTEMS`](@id JULIA_TIMING_SUBSYSTEMS)

Ermöglicht es Ihnen, Zonen für einen bestimmten Julia-Lauf zu aktivieren oder zu deaktivieren. Zum Beispiel wird durch das Setzen der Variablen auf `+GC,-INFERENCE` die `GC`-Zonen aktiviert und die `INFERENCE`-Zonen deaktiviert. Siehe [Dynamically Enabling and Disabling Zones](@ref).

### [`JULIA_GC_ALLOC_POOL`](@id JULIA_GC_ALLOC_POOL)

### [`JULIA_GC_ALLOC_OTHER`](@id JULIA_GC_ALLOC_OTHER)

### [`JULIA_GC_ALLOC_PRINT`](@id JULIA_GC_ALLOC_PRINT)

Wenn gesetzt, nehmen diese Umgebungsvariablen Zeichenfolgen an, die optional mit dem Zeichen `'r'` beginnen, gefolgt von einer Zeicheninterpolation einer durch Doppelpunkte getrennten Liste von drei vorzeichenbehafteten 64-Bit-Ganzzahlen (`int64_t`). Dieses Triple von Ganzzahlen `a:b:c` repräsentiert die arithmetische Folge `a`, `a + b`, `a + 2*b`, ... `c`.

  * Wenn es das `n`te Mal ist, dass `jl_gc_pool_alloc()` aufgerufen wurde, und `n` zur arithmetischen Folge gehört, die durch `$JULIA_GC_ALLOC_POOL` dargestellt wird, dann wird die Speicherbereinigung erzwungen.
  * Wenn es das `n`te Mal ist, dass `maybe_collect()` aufgerufen wurde, und `n` zur arithmetischen Folge gehört, die durch `$JULIA_GC_ALLOC_OTHER` dargestellt wird, dann wird die Speicherbereinigung erzwungen.
  * Wenn es das `n`te Mal ist, dass `jl_gc_collect()` aufgerufen wurde, und `n` zur arithmetischen Folge gehört, die durch `$JULIA_GC_ALLOC_PRINT` dargestellt wird, dann werden die Zählungen für die Anzahl der Aufrufe von `jl_gc_pool_alloc()` und `maybe_collect()` ausgegeben.

Wenn der Wert der Umgebungsvariable mit dem Zeichen `'r'` beginnt, wird das Intervall zwischen den Garbage-Collection-Ereignissen randomisiert.

!!! note
    Diese Umgebungsvariablen haben nur dann eine Wirkung, wenn Julia mit Debugging für die Speicherbereinigung kompiliert wurde (d. h. wenn `WITH_GC_DEBUG_ENV` in der Build-Konfiguration auf `1` gesetzt ist).


### [`JULIA_GC_NO_GENERATIONAL`](@id JULIA_GC_NO_GENERATIONAL)

Wenn auf etwas anderes als `0` gesetzt, führt der Julia-Garbage-Collector niemals "schnelle Durchläufe" des Speichers durch.

!!! note
    Diese Umgebungsvariable hat nur dann eine Wirkung, wenn Julia mit Debugging für die Speicherbereinigung kompiliert wurde (d. h. wenn `WITH_GC_DEBUG_ENV` in der Build-Konfiguration auf `1` gesetzt ist).


### [`JULIA_GC_WAIT_FOR_DEBUGGER`](@id JULIA_GC_WAIT_FOR_DEBUGGER)

Wenn auf etwas anderes als `0` gesetzt, wartet der Julia-Garbage-Collector darauf, dass ein Debugger angehängt wird, anstatt abzubrechen, wenn ein kritischer Fehler auftritt.

!!! note
    Diese Umgebungsvariable hat nur dann eine Wirkung, wenn Julia mit Debugging für die Speicherbereinigung kompiliert wurde (d. h. wenn `WITH_GC_DEBUG_ENV` in der Build-Konfiguration auf `1` gesetzt ist).


### [`ENABLE_JITPROFILING`](@id ENABLE_JITPROFILING)

Wenn auf etwas anderes als `0` gesetzt, erstellt der Compiler einen und registriert einen Ereignislistener für die Just-in-Time (JIT) Profilerstellung.

!!! note
    Diese Umgebungsvariable hat nur dann eine Wirkung, wenn Julia mit JIT-Profiling-Unterstützung kompiliert wurde, entweder mit

      * Intel's [VTune™ Amplifier](https://software.intel.com/en-us/vtune) (`USE_INTEL_JITEVENTS` auf `1` in der Build-Konfiguration gesetzt), oder
      * [OProfile](https://oprofile.sourceforge.io/news/) (`USE_OPROFILE_JITEVENTS` auf `1` in der Build-Konfiguration gesetzt).
      * [Perf](https://perf.wiki.kernel.org) (`USE_PERF_JITEVENTS` auf `1` in der Build-Konfiguration gesetzt). Diese Integration ist standardmäßig aktiviert.


### [`ENABLE_GDBLISTENER`](@id ENABLE_GDBLISTENER)

Wenn auf etwas anderes als `0` gesetzt, aktiviert dies die GDB-Registrierung von Julia-Code in Release-Builds. In Debug-Builds von Julia ist dies immer aktiviert. Es wird empfohlen, dies mit `-g 2` zu verwenden.

### [`JULIA_LLVM_ARGS`](@id JULIA_LLVM_ARGS)

Argument, die an das LLVM-Backend übergeben werden sollen.

### `JULIA_FALLBACK_REPL`

Zwingt den Fallback-REPL anstelle von REPL.jl.
