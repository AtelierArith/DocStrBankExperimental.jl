```
kron(A, B)
```

İki vektörün, matrisin veya sayının Kronecker çarpımını hesaplar.

Gerçek vektörler `v` ve `w` için, Kronecker çarpımı dış çarpımla `kron(v,w) == vec(w * transpose(v))` veya `w * transpose(v) == reshape(kron(v,w), (length(w), length(v)))` ile ilişkilidir. Bu ifadelerin sol ve sağ tarafındaki `v` ve `w` sıralamasının nasıl farklılık gösterdiğine dikkat edin (sütun-birincil depolama nedeniyle). Karmaşık vektörler için, dış çarpım `w * v'` de `v`'nin karmaşık eşleniği ile farklılık gösterir.

# Örnekler

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> B = [im 1; 1 -im]
2×2 Matrix{Complex{Int64}}:
 0+1im  1+0im
 1+0im  0-1im

julia> kron(A, B)
4×4 Matrix{Complex{Int64}}:
 0+1im  1+0im  0+2im  2+0im
 1+0im  0-1im  2+0im  0-2im
 0+3im  3+0im  0+4im  4+0im
 3+0im  0-3im  4+0im  0-4im

julia> v = [1, 2]; w = [3, 4, 5];

julia> w*transpose(v)
3×2 Matrix{Int64}:
 3   6
 4   8
 5  10

julia> reshape(kron(v,w), (length(w), length(v)))
3×2 Matrix{Int64}:
 3   6
 4   8
 5  10
```
