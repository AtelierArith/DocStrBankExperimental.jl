```
Base.identify_package(name::String)::Union{PkgId, Nothing}
Base.identify_package(where::Union{Module,PkgId}, name::String)::Union{PkgId, Nothing}
```

Identifizieren Sie das Paket anhand seines Namens aus dem aktuellen Umgebungsstapel, wobei seine `PkgId` zurückgegeben wird oder `nothing`, wenn es nicht gefunden werden kann.

Wenn nur das Argument `name` bereitgestellt wird, sucht es in jeder Umgebung im Stapel und deren benannten direkten Abhängigkeiten.

Das Argument `where` bietet den Kontext, von dem aus nach dem Paket gesucht werden soll: In diesem Fall wird zuerst überprüft, ob der Name mit dem Kontext selbst übereinstimmt, andernfalls werden alle rekursiven Abhängigkeiten (aus dem aufgelösten Manifest jeder Umgebung) durchsucht, bis der Kontext `where` gefunden wird, und von dort wird die Abhängigkeit mit dem entsprechenden Namen identifiziert.

```julia-repl
julia> Base.identify_package("Pkg") # Pkg ist eine Abhängigkeit der Standardumgebung
Pkg [44cfe95a-1eb2-52ea-b672-e2afdf69b78f]

julia> using LinearAlgebra

julia> Base.identify_package(LinearAlgebra, "Pkg") # Pkg ist keine Abhängigkeit von LinearAlgebra
```
