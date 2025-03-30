```
accumulate(op, A; dims::Integer, [init])
```

Aynı boyutta `A`'nın `dims` boyutu boyunca `op` işlemi. `dims` vektörler için isteğe bağlıdır. İsteğe bağlı olarak bir başlangıç değeri `init` anahtar argümanı ile sağlanabilir. Önceden tahsis edilmiş bir çıktı dizisi kullanmak için [`accumulate!`](@ref) ile performans ve çıktının hassasiyetini kontrol etmek (örneğin taşmayı önlemek için) için de bakın.

Yaygın işlemler için `accumulate`'in özel varyantları vardır, bkz. [`cumsum`](@ref), [`cumprod`](@ref). Tembel bir versiyon için bkz. [`Iterators.accumulate`](@ref).

!!! compat "Julia 1.5"
    Bir dizi olmayan bir yineleyici üzerinde `accumulate` en az Julia 1.5 gerektirir.


# Örnekler

```jldoctest
julia> accumulate(+, [1,2,3])
3-element Vector{Int64}:
 1
 3
 6

julia> accumulate(min, (1, -2, 3, -4, 5), init=0)
(0, -2, -2, -4, -4)

julia> accumulate(/, (2, 4, Inf), init=100)
(50.0, 12.5, 0.0)

julia> accumulate(=>, i^2 for i in 1:3)
3-element Vector{Any}:
          1
        1 => 4
 (1 => 4) => 9

julia> accumulate(+, fill(1, 3, 4))
3×4 Matrix{Int64}:
 1  4  7  10
 2  5  8  11
 3  6  9  12

julia> accumulate(+, fill(1, 2, 5), dims=2, init=100.0)
2×5 Matrix{Float64}:
 101.0  102.0  103.0  104.0  105.0
 101.0  102.0  103.0  104.0  105.0
```
