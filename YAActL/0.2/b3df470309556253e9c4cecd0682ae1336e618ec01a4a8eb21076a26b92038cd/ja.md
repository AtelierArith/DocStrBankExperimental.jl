```
parallel(size=32; taskref=nothing)
```

`spawn=true`の[`LinkParams`](@ref)を返します。

# 例

```julia
julia> using YAActL, .Threads

julia> myactor = Actor(parallel(), threadid);

julia> call!(myactor)
2
```
