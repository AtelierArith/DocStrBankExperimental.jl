```
@fetchfrom
```

`fetch(@spawnat p expr)` ile eşdeğerdir. [`fetch`](@ref) ve [`@spawnat`](@ref) bakınız.

# Örnekler

```julia-repl
julia> addprocs(3);

julia> @fetchfrom 2 myid()
2

julia> @fetchfrom 4 myid()
4
```
