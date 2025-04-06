```
isdiag(A) -> Bool
```

Bir matrisin, `iszero(A[i,j])` ifadesinin `i == j` olmadığı sürece doğru olduğu anlamında diyagonal olup olmadığını test eder. `A`'nın kare olması gerekmez; eğer bunu da kontrol etmek istiyorsanız, `size(A, 1) == size(A, 2)` kontrolünü yapmanız gerekir.

# Örnekler

```jldoctest
julia> a = [1 2; 2 -1]
2×2 Matrix{Int64}:
 1   2
 2  -1

julia> isdiag(a)
false

julia> b = [im 0; 0 -im]
2×2 Matrix{Complex{Int64}}:
 0+1im  0+0im
 0+0im  0-1im

julia> isdiag(b)
true

julia> c = [1 0 0; 0 2 0]
2×3 Matrix{Int64}:
 1  0  0
 0  2  0

julia> isdiag(c)
true

julia> d = [1 0 0; 0 2 3]
2×3 Matrix{Int64}:
 1  0  0
 0  2  3

julia> isdiag(d)
false
```
