```
WorkerConfig
```

Typ, der von [`ClusterManager`](@ref)s verwendet wird, um die zu ihren Clustern hinzugefügten Worker zu steuern. Einige Felder werden von allen Cluster-Managern verwendet, um auf einen Host zuzugreifen:

  * `io` – die Verbindung, die verwendet wird, um auf den Worker zuzugreifen (ein Subtyp von `IO` oder `Nothing`)
  * `host` – die Hostadresse (entweder ein `String` oder `Nothing`)
  * `port` – der Port auf dem Host, der verwendet wird, um eine Verbindung zum Worker herzustellen (entweder ein `Int` oder `Nothing`)

Einige werden vom Cluster-Manager verwendet, um Worker zu einem bereits initialisierten Host hinzuzufügen:

  * `count` – die Anzahl der Worker, die auf dem Host gestartet werden sollen
  * `exename` – der Pfad zur Julia-Ausführungsdatei auf dem Host, standardmäßig `"$(Sys.BINDIR)/julia"` oder `"$(Sys.BINDIR)/julia-debug"`
  * `exeflags` – Flags, die beim Starten von Julia remote verwendet werden

Das Feld `userdata` wird verwendet, um Informationen für jeden Worker von externen Managern zu speichern.

Einige Felder werden von `SSHManager` und ähnlichen Managern verwendet:

  * `tunnel` – `true` (Tunneling verwenden), `false` (kein Tunneling verwenden) oder [`nothing`](@ref) (Standard für den Manager verwenden)
  * `multiplex` – `true` (SSH-Multiplexing für Tunneling verwenden) oder `false`
  * `forward` – die Weiterleitungsoption, die für die `-L`-Option von ssh verwendet wird
  * `bind_addr` – die Adresse auf dem Remote-Host, an die gebunden werden soll
  * `sshflags` – Flags, die beim Herstellen der SSH-Verbindung verwendet werden
  * `max_parallel` – die maximale Anzahl von Workern, die parallel auf dem Host verbunden werden sollen

Einige Felder werden sowohl von `LocalManager`s als auch von `SSHManager`s verwendet:

  * `connect_at` – bestimmt, ob dies ein Worker-zu-Worker- oder Driver-zu-Worker-Setup-Aufruf ist
  * `process` – der Prozess, der verbunden werden soll (normalerweise weist der Manager dies während [`addprocs`](@ref) zu)
  * `ospid` – die Prozess-ID gemäß dem Host-OS, die verwendet wird, um Worker-Prozesse zu unterbrechen
  * `environ` – privates Wörterbuch, das von Local/SSH-Managern verwendet wird, um temporäre Informationen zu speichern
  * `ident` – Worker, wie er vom [`ClusterManager`](@ref) identifiziert wird
  * `connect_idents` – Liste der Worker-IDs, mit denen der Worker verbunden werden muss, wenn eine benutzerdefinierte Topologie verwendet wird
  * `enable_threaded_blas` – `true`, `false` oder `nothing`, ob auf den Workern threaded BLAS verwendet werden soll oder nicht
