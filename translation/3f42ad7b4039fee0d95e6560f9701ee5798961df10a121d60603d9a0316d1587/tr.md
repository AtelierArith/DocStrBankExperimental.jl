```
Array{T}(undef, dims)
Array{T,N}(undef, dims)
```

Başlatılmamış bir `N`-boyutlu [`Array`](@ref) oluşturur ve `T` türünde elemanlar içerir. `N`, `Array{T,N}(undef, dims)` şeklinde açıkça sağlanabilir veya `dims`'in uzunluğu veya sayısı ile belirlenebilir. `dims`, her boyuttaki uzunluklara karşılık gelen bir demet veya bir dizi tam sayı argümanı olabilir. Eğer `N` açıkça sağlanmışsa, o zaman `dims`'in uzunluğu veya sayısı ile eşleşmelidir. Burada [`undef`](@ref) [`UndefInitializer`](@ref)dır.

# Örnekler

```julia-repl
julia> A = Array{Float64, 2}(undef, 2, 3) # N açıkça verilmiş
2×3 Matrix{Float64}:
 6.90198e-310  6.90198e-310  6.90198e-310
 6.90198e-310  6.90198e-310  0.0

julia> B = Array{Float64}(undef, 4) # N girdi ile belirlenmiş
4-element Vector{Float64}:
   2.360075077e-314
 NaN
   2.2671131793e-314
   2.299821756e-314

julia> similar(B, 2, 4, 1) # typeof(B) kullan, ve verilen boyutu
2×4×1 Array{Float64, 3}:
[:, :, 1] =
 2.26703e-314  2.26708e-314  0.0           2.80997e-314
 0.0           2.26703e-314  2.26708e-314  0.0
```
