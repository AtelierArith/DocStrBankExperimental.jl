```
UndefInitializer
```

Dizi başlatmada kullanılan tekil tür, dizi oluşturucu çağrısının başlatılmamış bir dizi istediğini belirtir. Ayrıca [`undef`](@ref) için bir takma ad olan `UndefInitializer()`'a da bakın.

# Örnekler

```julia-repl
julia> Array{Float64, 1}(UndefInitializer(), 3)
3-element Array{Float64, 1}:
 2.2752528595e-314
 2.202942107e-314
 2.275252907e-314
```
