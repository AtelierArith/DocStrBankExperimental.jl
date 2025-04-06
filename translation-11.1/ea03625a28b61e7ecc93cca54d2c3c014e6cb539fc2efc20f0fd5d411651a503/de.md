```
addprocs(machines; tunnel=false, sshflags=``, max_parallel=10, kwargs...) -> Liste der Prozessidentifikatoren
```

Fügen Sie Arbeitsprozesse auf Remote-Maschinen über SSH hinzu. Die Konfiguration erfolgt über Schlüsselwortargumente (siehe unten). Insbesondere kann das Schlüsselwort `exename` verwendet werden, um den Pfad zur `julia`-Binärdatei auf der Remote-Maschine(n) anzugeben.

`machines` ist ein Vektor von "Maschinenspezifikationen", die als Strings der Form `[user@]host[:port] [bind_addr[:port]]` angegeben werden. `user` ist standardmäßig der aktuelle Benutzer und `port` der Standard-SSH-Port. Wenn `[bind_addr[:port]]` angegeben ist, stellen andere Arbeiter eine Verbindung zu diesem Arbeiter über die angegebene `bind_addr` und `port` her.

Es ist möglich, mehrere Prozesse auf einem Remote-Host zu starten, indem ein Tupel im `machines`-Vektor oder die Form `(machine_spec, count)` verwendet wird, wobei `count` die Anzahl der zu startenden Arbeiter auf dem angegebenen Host ist. Das Übergeben von `:auto` als Arbeiteranzahl startet so viele Arbeiter wie CPU-Threads auf dem Remote-Host.

**Beispiele**:

```julia
addprocs([
    "remote1",               # ein Arbeiter auf 'remote1', der sich mit dem aktuellen Benutzernamen anmeldet
    "user@remote2",          # ein Arbeiter auf 'remote2', der sich mit dem Benutzernamen 'user' anmeldet
    "user@remote3:2222",     # SSH-Port auf '2222' für 'remote3' angeben
    ("user@remote4", 4),     # 4 Arbeiter auf 'remote4' starten
    ("user@remote5", :auto), # so viele Arbeiter wie CPU-Threads auf 'remote5' starten
])
```

**Schlüsselwortargumente**:

  * `tunnel`: wenn `true`, wird SSH-Tunneling verwendet, um sich vom Master-Prozess mit dem Arbeiter zu verbinden. Standard ist `false`.
  * `multiplex`: wenn `true`, wird SSH-Multiplexing für SSH-Tunneling verwendet. Standard ist `false`.
  * `ssh`: der Name oder Pfad des SSH-Client-Executables, das zum Starten der Arbeiter verwendet wird. Standard ist `"ssh"`.
  * `sshflags`: gibt zusätzliche SSH-Optionen an, z.B. ```sshflags=`-i /home/foo/bar.pem` ```
  * `max_parallel`: gibt die maximale Anzahl von Arbeitern an, die parallel zu einem Host verbunden sind. Standardmäßig 10.
  * `shell`: gibt den Typ der Shell an, mit der SSH sich bei den Arbeitern verbindet.

      * `shell=:posix`: eine POSIX-kompatible Unix/Linux-Shell (sh, ksh, bash, dash, zsh usw.). Der Standard.
      * `shell=:csh`: eine Unix C-Shell (csh, tcsh).
      * `shell=:wincmd`: Microsoft Windows `cmd.exe`.
  * `dir`: gibt das Arbeitsverzeichnis auf den Arbeitern an. Standardmäßig das aktuelle Verzeichnis des Hosts (wie von `pwd()` gefunden).
  * `enable_threaded_blas`: wenn `true`, wird BLAS in mehreren Threads in hinzugefügten Prozessen ausgeführt. Standard ist `false`.
  * `exename`: Name der `julia`-Executable. Standard ist `"$(Sys.BINDIR)/julia"` oder `"$(Sys.BINDIR)/julia-debug"` je nach Fall. Es wird empfohlen, auf allen Remote-Maschinen eine gemeinsame Julia-Version zu verwenden, da sonst die Serialisierung und der Codevertrieb fehlschlagen könnten.
  * `exeflags`: zusätzliche Flags, die an die Arbeiterprozesse übergeben werden.
  * `topology`: Gibt an, wie die Arbeiter miteinander verbunden sind. Das Senden einer Nachricht zwischen nicht verbundenen Arbeitern führt zu einem Fehler.

      * `topology=:all_to_all`: Alle Prozesse sind miteinander verbunden. Der Standard.
      * `topology=:master_worker`: Nur der Treiberprozess, d.h. `pid` 1, verbindet sich mit den Arbeitern. Die Arbeiter verbinden sich nicht untereinander.
      * `topology=:custom`: Die `launch`-Methode des Cluster-Managers gibt die Verbindungstopologie über die Felder `ident` und `connect_idents` in `WorkerConfig` an. Ein Arbeiter mit einer Cluster-Manager-Identität `ident` verbindet sich mit allen Arbeitern, die in `connect_idents` angegeben sind.
  * `lazy`: Anwendbar nur mit `topology=:all_to_all`. Wenn `true`, werden die Verbindungen zwischen Arbeitern faul eingerichtet, d.h. sie werden beim ersten Remote-Aufruf zwischen Arbeitern eingerichtet. Standard ist `true`.
  * `env`: Stellen Sie ein Array von String-Paaren wie `env=["JULIA_DEPOT_PATH"=>"/depot"]` bereit, um zu verlangen, dass Umgebungsvariablen auf der Remote-Maschine gesetzt werden. Standardmäßig wird nur die Umgebungsvariable `JULIA_WORKER_TIMEOUT` automatisch von der lokalen in die Remote-Umgebung übergeben.
  * `cmdline_cookie`: Übergeben Sie das Authentifizierungscookie über die `--worker`-Befehlszeilenoption. Das (sicherere) Standardverhalten, das Cookie über SSH stdio zu übergeben, kann bei Windows-Arbeitern, die ältere (vor ConPTY) Julia- oder Windows-Versionen verwenden, hängen bleiben, in diesem Fall bietet `cmdline_cookie=true` eine Umgehungslösung.

!!! compat "Julia 1.6"
    Die Schlüsselwortargumente `ssh`, `shell`, `env` und `cmdline_cookie` wurden in Julia 1.6 hinzugefügt.


Umgebungsvariablen:

Wenn der Master-Prozess innerhalb von 60,0 Sekunden keine Verbindung zu einem neu gestarteten Arbeiter herstellen kann, betrachtet der Arbeiter dies als eine fatale Situation und beendet sich. Dieses Timeout kann über die Umgebungsvariable `JULIA_WORKER_TIMEOUT` gesteuert werden. Der Wert von `JULIA_WORKER_TIMEOUT` im Master-Prozess gibt die Anzahl der Sekunden an, die ein neu gestarteter Arbeiter auf die Herstellung der Verbindung wartet.
