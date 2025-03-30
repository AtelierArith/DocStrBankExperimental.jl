```
take!(c::Channel)
```

Bir [`Channel`](@ref) içinden sırayla bir değeri kaldırır ve döndürür. Veri mevcut olana kadar engeller. Tamponlanmamış kanallar için, başka bir görev tarafından bir [`put!`](@ref) gerçekleştirilene kadar engeller.

# Örnekler

Tamponlu kanal:

```jldoctest
julia> c = Channel(1);

julia> put!(c, 1);

julia> take!(c)
1
```

Tamponsuz kanal:

```jldoctest
julia> c = Channel(0);

julia> task = Task(() -> put!(c, 1));

julia> schedule(task);

julia> take!(c)
1
```
