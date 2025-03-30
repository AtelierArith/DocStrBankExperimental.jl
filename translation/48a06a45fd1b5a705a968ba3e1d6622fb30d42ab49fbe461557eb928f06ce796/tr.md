```
undef
```

`UndefInitializer()` için bir takma addır; bu, dizi başlatmada, dizi oluşturucu çağrısının başlatılmamış bir dizi istediğini belirtmek için kullanılan [`UndefInitializer`](@ref) tekil türünün bir örneğini oluşturur.

Ayrıca bakınız: [`missing`](@ref), [`similar`](@ref).

# Örnekler

```julia-repl
julia> Array{Float64, 1}(undef, 3)
3-element Vector{Float64}:
 2.2752528595e-314
 2.202942107e-314
 2.275252907e-314
```
