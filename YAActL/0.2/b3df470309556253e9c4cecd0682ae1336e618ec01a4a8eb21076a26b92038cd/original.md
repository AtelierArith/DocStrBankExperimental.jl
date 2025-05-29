```
parallel(size=32; taskref=nothing)
```

Return [`LinkParams`](@ref) with `spawn=true`.

# Example

```julia
julia> using YAActL, .Threads

julia> myactor = Actor(parallel(), threadid);

julia> call!(myactor)
2
```
