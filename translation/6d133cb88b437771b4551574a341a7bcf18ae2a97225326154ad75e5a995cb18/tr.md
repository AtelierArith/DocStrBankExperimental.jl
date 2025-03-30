```
sprandn([rng][,Type],m[,n],p::AbstractFloat)
```

Uzunluğu `m` olan rastgele seyrek bir vektör veya `m` x `n` boyutunda seyrek bir matris oluşturur; burada herhangi bir girişin sıfır olmama olasılığı `p` olarak belirtilmiştir ve sıfır olmayan değerler normal dağılımdan örneklenir. İsteğe bağlı `rng` argümanı, rastgele sayı üreteciyi belirtir, bkz. [Rastgele Sayılar](@ref).

!!! compat "Julia 1.1"
    Çıktı eleman türünü `Type` belirtmek en az Julia 1.1 gerektirir.


# Örnekler

```jldoctest; setup = :(using Random; Random.seed!(0))
julia> sprandn(2, 2, 0.75)
2×2 SparseMatrixCSC{Float64, Int64} with 3 stored entries:
 -1.20577     ⋅
  0.311817  -0.234641
```
