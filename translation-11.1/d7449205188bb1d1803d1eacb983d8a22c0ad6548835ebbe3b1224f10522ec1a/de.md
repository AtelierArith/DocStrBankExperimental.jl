```
addprocs(np::Integer=Sys.CPU_THREADS; restrict=true, kwargs...) -> Liste der Prozess-Identifikatoren
```

Starten Sie `np` Arbeiter auf dem lokalen Host mit dem integrierten `LocalManager`.

Lokale Arbeiter erben die aktuelle Paketumgebung (d.h. aktives Projekt, [`LOAD_PATH`](@ref) und [`DEPOT_PATH`](@ref)) vom Hauptprozess.

!!! warning
    Beachten Sie, dass Arbeiter kein `~/.julia/config/startup.jl` Startskript ausführen und ihren globalen Zustand (wie Befehlszeilenoptionen, globale Variablen, neue Methodendefinitionen und geladene Module) nicht mit anderen laufenden Prozessen synchronisieren.


**Schlüsselwortargumente**:

  * `restrict::Bool`: wenn `true` (Standard) ist die Bindung auf `127.0.0.1` beschränkt.
  * `dir`, `exename`, `exeflags`, `env`, `topology`, `lazy`, `enable_threaded_blas`: derselbe Effekt wie bei `SSHManager`, siehe Dokumentation für [`addprocs(machines::AbstractVector)`](@ref).

!!! compat "Julia 1.9"
    Das Erben der Paketumgebung und das Schlüsselwortargument `env` wurden in Julia 1.9 hinzugefügt.

