```
procs()
```

Tüm işlem tanımlayıcılarının bir listesini döndürür, pid 1 dahil (bu [`workers()`](@ref) tarafından dahil edilmez).

# Örnekler

```julia-repl
$ julia -p 2

julia> procs()
3-element Array{Int64,1}:
 1
 2
 3
```
