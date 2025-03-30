```
maximum(f, A::AbstractArray; dims)
```

Verilen boyutlar üzerinde bir dizi içindeki her bir eleman için `f` fonksiyonunu çağırarak maksimum değeri hesaplayın.

# Örnekler

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> maximum(abs2, A, dims=1)
1×2 Matrix{Int64}:
 9  16

julia> maximum(abs2, A, dims=2)
2×1 Matrix{Int64}:
  4
 16
```
