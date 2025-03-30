```
accumulate!(op, B, A; [dims], [init])
```

Kümülatif işlem `op`'u `A` üzerinde `dims` boyutu boyunca gerçekleştirir ve sonucu `B`'ye kaydeder. Vektörler için `dims` sağlamak isteğe bağlıdır. Eğer `init` anahtar kelime argümanı verilirse, değeri birikimi başlatmak için kullanılır.

!!! warning
    Herhangi bir değiştirilmiş argümanın, başka bir argümanla bellek paylaşması durumunda davranış beklenmedik olabilir.


Ayrıca bkz. [`accumulate`](@ref), [`cumsum!`](@ref), [`cumprod!`](@ref).

# Örnekler

```jldoctest
julia> x = [1, 0, 2, 0, 3];

julia> y = rand(5);

julia> accumulate!(+, y, x);

julia> y
5-element Vector{Float64}:
 1.0
 1.0
 3.0
 3.0
 6.0

julia> A = [1 2 3; 4 5 6];

julia> B = similar(A);

julia> accumulate!(-, B, A, dims=1)
2×3 Matrix{Int64}:
  1   2   3
 -3  -3  -3

julia> accumulate!(*, B, A, dims=2, init=10)
2×3 Matrix{Int64}:
 10   20    60
 40  200  1200
```
