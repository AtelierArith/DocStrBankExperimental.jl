```
minimum(f, A::AbstractArray; dims)
```

Verilen boyutlar üzerinde bir dizi içindeki her bir eleman üzerinde `f` fonksiyonunu çağırarak minimum değeri hesaplar.

# Örnekler

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> minimum(abs2, A, dims=1)
1×2 Matrix{Int64}:
 1  4

julia> minimum(abs2, A, dims=2)
2×1 Matrix{Int64}:
 1
 9
```
