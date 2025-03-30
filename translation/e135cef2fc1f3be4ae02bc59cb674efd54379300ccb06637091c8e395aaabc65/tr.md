```
isready(c::Channel)
```

Bir [`Channel`](@ref) içinde bir değer olup olmadığını belirler. Hemen döner, engellemez.

Tamponlanmamış kanallar için, [`put!`](@ref) üzerinde bekleyen görevler varsa `true` döner.

# Örnekler

Tamponlu kanal:

```jldoctest
julia> c = Channel(1);

julia> isready(c)
false

julia> put!(c, 1);

julia> isready(c)
true
```

Tamponlanmamış kanal:

```jldoctest
julia> c = Channel();

julia> isready(c)  # hiçbir görev put! için beklemiyor!
false

julia> task = Task(() -> put!(c, 1));

julia> schedule(task);  # bir put! görevini planla

julia> isready(c)
true
```
