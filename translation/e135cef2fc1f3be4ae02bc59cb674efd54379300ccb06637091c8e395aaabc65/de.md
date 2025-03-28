```
isready(c::Channel)
```

Bestimmt, ob ein [`Channel`](@ref) einen Wert gespeichert hat. Gibt sofort zurück, blockiert nicht.

Für unbuffered Channels gibt es `true` zurück, wenn Aufgaben warten, um einen [`put!`](@ref) auszuführen.

# Beispiele

Buffered Channel:

```jldoctest
julia> c = Channel(1);

julia> isready(c)
false

julia> put!(c, 1);

julia> isready(c)
true
```

Unbuffered Channel:

```jldoctest
julia> c = Channel();

julia> isready(c)  # keine Aufgaben warten, um zu put!
false

julia> task = Task(() -> put!(c, 1));

julia> schedule(task);  # eine put! Aufgabe planen

julia> isready(c)
true
```
