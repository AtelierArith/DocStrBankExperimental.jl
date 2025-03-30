```
minimum(A::AbstractArray; dims)
```

Verilen boyutlar üzerinde bir dizinin minimum değerini hesaplar. İki veya daha fazla argümanın minimumunu almak için [`min(a,b)`](@ref) fonksiyonuna da bakın; bu, dizilere `min.(a,b)` ile eleman bazında uygulanabilir.

Ayrıca bakınız: [`minimum!`](@ref), [`extrema`](@ref), [`findmin`](@ref), [`argmin`](@ref).

# Örnekler

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> minimum(A, dims=1)
1×2 Matrix{Int64}:
 1  2

julia> minimum(A, dims=2)
2×1 Matrix{Int64}:
 1
 3
```
