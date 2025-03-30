```
randn([rng=default_rng()], [T=Float64], [dims...])
```

0 ortalama ve 1 standart sapmaya sahip `T` türünde normal dağılımlı rastgele bir sayı üretir. Opsiyonel `dims` argüman(lar)ı verildiğinde, bu türden sayıların `dims` boyutunda bir dizisini üretir. Julia'nın standart kütüphanesi, [`rand`](@ref) uygulayan herhangi bir kayan nokta türü için `randn`'ı destekler; örneğin, `Base` türleri [`Float16`](@ref), [`Float32`](@ref), [`Float64`](@ref) (varsayılan) ve [`BigFloat`](@ref) ile birlikte bunların [`Complex`](@ref) karşıtları.

(`T` karmaşık olduğunda, değerler, varyansı 1 olan dairesel simetrik karmaşık normal dağılımdan çekilir; bu, reel ve sanal kısımların sıfır ortalama ve `1/2` varyansa sahip bağımsız normal dağılıma sahip olduğu anlamına gelir).

Yerinde işlem yapmak için [`randn!`](@ref) ile de bakabilirsiniz.

# Örnekler

Tek bir rastgele sayı üretme (varsayılan `Float64` türü ile):

```julia-repl
julia> randn()
-0.942481877315864
```

Normal rastgele sayıların bir matrisini üretme (varsayılan `Float64` türü ile):

```julia-repl
julia> randn(2,3)
2×3 Matrix{Float64}:
  1.18786   -0.678616   1.49463
 -0.342792  -0.134299  -1.45005
```

Kullanıcı tanımlı bir tohum ile rastgele sayı üreteci `rng`'yi ayarlama (tekrarlanabilir sayılar için) ve bunu kullanarak rastgele bir `Float32` sayısı veya `ComplexF32` rastgele sayılardan oluşan bir matris üretme:

```jldoctest
julia> using Random

julia> rng = Xoshiro(123);

julia> randn(rng, Float32)
-0.6457307f0

julia> randn(rng, ComplexF32, (2, 3))
2×3 Matrix{ComplexF32}:
  -1.03467-1.14806im  0.693657+0.056538im   0.291442+0.419454im
 -0.153912+0.34807im    1.0954-0.948661im  -0.543347-0.0538589im
```
