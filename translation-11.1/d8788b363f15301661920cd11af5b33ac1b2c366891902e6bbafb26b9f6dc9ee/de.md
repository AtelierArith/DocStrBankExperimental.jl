```
take!(c::Channel)
```

Entfernt und gibt einen Wert aus einem [`Channel`](@ref) in der richtigen Reihenfolge zurück. Blockiert, bis Daten verfügbar sind. Bei unpufferten Kanälen blockiert es, bis ein [`put!`](@ref) von einer anderen Aufgabe ausgeführt wird.

# Beispiele

Pufferkanal:

```jldoctest
julia> c = Channel(1);

julia> put!(c, 1);

julia> take!(c)
1
```

Unpufferter Kanal:

```jldoctest
julia> c = Channel(0);

julia> task = Task(() -> put!(c, 1));

julia> schedule(task);

julia> take!(c)
1
```
