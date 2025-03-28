```
DEPOT_PATH
```

Ein Stapel von "Depot"-Standorten, an denen der Paketmanager sowie Julias Code-Lade-Mechanismen nach Paketregistern, installierten Paketen, benannten Umgebungen, Repo-Kopien, zwischengespeicherten kompilierten Paketbildern und Konfigurationsdateien suchen. Standardmäßig umfasst es:

1. `~/.julia`, wobei `~` das Benutzerverzeichnis ist, wie es im System angemessen ist;
2. ein architekturspezifisches gemeinsames Systemverzeichnis, z. B. `/usr/local/share/julia`;
3. ein architekturunabhängiges gemeinsames Systemverzeichnis, z. B. `/usr/share/julia`.

Also könnte `DEPOT_PATH` sein:

```julia
[joinpath(homedir(), ".julia"), "/usr/local/share/julia", "/usr/share/julia"]
```

Der erste Eintrag ist das "Benutzerdepot" und sollte vom aktuellen Benutzer beschreibbar und besessen sein. Das Benutzerdepot ist der Ort, an dem: Registrierungen geklont, neue Paketversionen installiert, benannte Umgebungen erstellt und aktualisiert, Paket-Repos geklont, neu kompilierte Paketbilddateien gespeichert, Protokolldateien geschrieben, Entwicklungs-Pakete standardmäßig ausgecheckt und globale Konfigurationsdaten gespeichert werden. Spätere Einträge im Depotpfad werden als schreibgeschützt behandelt und sind geeignet für Registrierungen, Pakete usw., die von Systemadministratoren installiert und verwaltet werden.

`DEPOT_PATH` wird basierend auf der [`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH) Umgebungsvariable befüllt, wenn sie gesetzt ist.

## DEPOT_PATH-Inhalte

Jeder Eintrag in `DEPOT_PATH` ist ein Pfad zu einem Verzeichnis, das Unterverzeichnisse enthält, die von Julia für verschiedene Zwecke verwendet werden. Hier ist eine Übersicht über einige der Unterverzeichnisse, die in einem Depot existieren können:

  * `artifacts`: Enthält Inhalte, die Pakete verwenden, für die Pkg die Installation verwaltet.
  * `clones`: Enthält vollständige Klone von Paket-Repos. Wird von `Pkg.jl` verwaltet und als Cache verwendet.
  * `config`: Enthält julia-spezifische Konfigurationen wie eine `startup.jl`
  * `compiled`: Enthält vorkompilierte `*.ji`-Dateien für Pakete. Wird von Julia verwaltet.
  * `dev`: Standardverzeichnis für `Pkg.develop`. Wird von `Pkg.jl` und dem Benutzer verwaltet.
  * `environments`: Standard-Paketumgebungen. Zum Beispiel die globale Umgebung für eine bestimmte Julia-Version. Wird von `Pkg.jl` verwaltet.
  * `logs`: Enthält Protokolle von `Pkg`- und `REPL`-Operationen. Wird von `Pkg.jl` und `Julia` verwaltet.
  * `packages`: Enthält Pakete, von denen einige explizit installiert wurden und einige implizite Abhängigkeiten sind. Wird von `Pkg.jl` verwaltet.
  * `registries`: Enthält Paketregistrierungen. Standardmäßig nur `General`. Wird von `Pkg.jl` verwaltet.
  * `scratchspaces`: Enthält Inhalte, die ein Paket selbst über das [`Scratch.jl`](https://github.com/JuliaPackaging/Scratch.jl) Paket installiert. `Pkg.gc()` löscht Inhalte, von denen bekannt ist, dass sie nicht verwendet werden.

!!! note
    Pakete, die Inhalte speichern möchten, sollten das Unterverzeichnis `scratchspaces` über [`Scratch.jl`](https://github.com/JuliaPackaging/Scratch.jl) verwenden, anstatt neue Unterverzeichnisse im Depotstamm zu erstellen.


Siehe auch [`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH) und [Code Loading](@ref code-loading).
