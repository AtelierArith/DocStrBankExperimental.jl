```
wait(c::Channel)
```

`Channel` [`isready`](@ref) olana kadar engeller.

```jldoctest
julia> c = Channel(1);

julia> isready(c)
false

julia> task = Task(() -> wait(c));

julia> schedule(task);

julia> istaskdone(task)  # görev engellendi çünkü kanal hazır değil
false

julia> put!(c, 1);

julia> istaskdone(task)  # görev şimdi engellenmedi
true
```
