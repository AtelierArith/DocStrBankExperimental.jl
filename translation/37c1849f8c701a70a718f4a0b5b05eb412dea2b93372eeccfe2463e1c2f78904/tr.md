```
prod(f, A::AbstractArray; dims)
```

Verilen boyutlar üzerinde bir dizinin her bir elemanına `f` fonksiyonunu çağırarak elde edilen sonuçları çarpın.

# Örnekler

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> prod(abs2, A, dims=1)
1×2 Matrix{Int64}:
 9  64

julia> prod(abs2, A, dims=2)
2×1 Matrix{Int64}:
   4
 144
```
