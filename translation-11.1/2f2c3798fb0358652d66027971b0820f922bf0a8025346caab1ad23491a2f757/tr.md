```
maximum(A::AbstractArray; dims)
```

Verilen boyutlar üzerinde bir dizinin maksimum değerini hesaplayın. İki veya daha fazla argümanın maksimumunu almak için [`max(a,b)`](@ref) fonksiyonuna da bakın; bu, dizilere `max.(a,b)` ile eleman bazında uygulanabilir.

Ayrıca bakınız: [`maximum!`](@ref), [`extrema`](@ref), [`findmax`](@ref), [`argmax`](@ref).

# Örnekler

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> maximum(A, dims=1)
1×2 Matrix{Int64}:
 3  4

julia> maximum(A, dims=2)
2×1 Matrix{Int64}:
 2
 4
```
