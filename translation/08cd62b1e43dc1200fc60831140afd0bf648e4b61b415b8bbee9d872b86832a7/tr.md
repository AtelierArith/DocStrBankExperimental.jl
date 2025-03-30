```
sprand([rng],[T::Type],m,[n],p::AbstractFloat)
sprand([rng],m,[n],p::AbstractFloat,[rfn=rand])
```

Rastgele uzunlukta `m` seyrek vektör veya `m` x `n` seyrek matris oluşturur; burada herhangi bir elemanın sıfırdan farklı olma olasılığı bağımsız olarak `p` ile verilir (ve dolayısıyla sıfırdan farklıların ortalama yoğunluğu da tam olarak `p`'dir). İsteğe bağlı `rng` argümanı, rastgele sayı üreteci belirtir, bkz. [Rastgele Sayılar](@ref). İsteğe bağlı `T` argümanı, varsayılan olarak `Float64` olan eleman türünü belirtir.

Varsayılan olarak, sıfırdan farklı değerler, [`rand`](@ref) fonksiyonu kullanılarak, yani `rand(T)` veya `rng` sağlanmışsa `rand(rng, T)` ile, bir uniform dağılımdan örneklenir; varsayılan `T=Float64` için bu, sıfırdan farklı değerlerin `[0,1)` aralığında uniform olarak örneklenmesi anlamına gelir.

Sıfırdan farklı değerleri farklı bir dağılımdan örneklemek için, `rand` yerine özel bir `rfn` fonksiyonu geçebilirsiniz. Bu, istenen dağılımdan örneklenen `k` rastgele sayıdan oluşan bir dizi döndüren bir fonksiyon `rfn(k)` olmalıdır; alternatif olarak, `rng` sağlanmışsa, bunun yerine `rfn(rng, k)` olmalıdır.

# Örnekler

```jldoctest; setup = :(using Random; Random.seed!(1234))
julia> sprand(Bool, 2, 2, 0.5)
2×2 SparseMatrixCSC{Bool, Int64} ile 2 saklanan giriş:
 1  1
 ⋅  ⋅

julia> sprand(Float64, 3, 0.75)
3-elemanlı SparseVector{Float64, Int64} ile 2 saklanan giriş:
  [1]  =  0.795547
  [2]  =  0.49425
```
