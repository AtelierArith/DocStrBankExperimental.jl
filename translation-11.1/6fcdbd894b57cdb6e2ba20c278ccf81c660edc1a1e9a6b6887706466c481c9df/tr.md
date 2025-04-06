```
rand([rng=default_rng()], [S], [dims...])
```

`S` tarafından belirtilen değerler kümesinden rastgele bir öğe veya rastgele öğeler dizisi seçin; `S` şunlar olabilir:

  * indekslenebilir bir koleksiyon (örneğin `1:9` veya `('x', "y", :z)`)
  * bir `AbstractDict` veya `AbstractSet` nesnesi
  * bir dize (karakterler koleksiyonu olarak kabul edilir), veya
  * aşağıdaki listeden bir tür, belirtilen değerler kümesine karşılık gelir

      * somut tam sayı türleri `typemin(S):typemax(S)` aralığından örnek alır (desteklenmeyen [`BigInt`](@ref) hariç)
      * somut kayan nokta türleri `[0, 1)` aralığından örnek alır
      * `Complex{T}` türündeki somut karmaşık türler, `T` örneklenebilir bir türse, `T`'ye karşılık gelen değerler kümesinden bağımsız olarak gerçek ve hayali bileşenlerini alır, ancak `T` örneklenebilir değilse desteklenmez.
      * tüm `<:AbstractChar` türleri geçerli Unicode skalarları kümesinden örnek alır
      * kullanıcı tanımlı bir tür ve değerler kümesi; uygulama rehberi için lütfen [Random API'ye Bağlanma](@ref rand-api-hook) bölümüne bakın
      * bilinen boyutta bir demet türü ve `S`'nin her parametresi kendisi örneklenebilir bir türse; `S` türünde bir değer döndürün. `Tuple{Vararg{T}}` (bilinmeyen boyut) ve `Tuple{1:2}` (bir değerle parametrelenmiş) gibi demet türlerinin desteklenmediğini unutmayın.
      * `Pair` türü, örneğin `Pair{X, Y}` böylece `rand` için `X` ve `Y` tanımlıysa, rastgele çiftler üretilir.

`S` varsayılan olarak [`Float64`](@ref) olarak ayarlanmıştır. Opsiyonel `rng` dışında yalnızca bir argüman geçirildiğinde ve bu bir `Tuple` olduğunda, değerler koleksiyonu (`S`) olarak yorumlanır ve `dims` olarak değil.

Normal dağılımlı sayılar için [`randn`](@ref) ve yerinde eşdeğerleri için [`rand!`](@ref) ve [`randn!`](@ref) bölümlerine de bakın.

!!! compat "Julia 1.1"
    `S`'nin bir demet olarak desteklenmesi en az Julia 1.1 gerektirir.


!!! compat "Julia 1.11"
    `S`'nin bir `Tuple` türü olarak desteklenmesi en az Julia 1.11 gerektirir.


# Örnekler

```julia-repl
julia> rand(Int, 2)
2-element Array{Int64,1}:
 1339893410598768192
 1575814717733606317

julia> using Random

julia> rand(Xoshiro(0), Dict(1=>2, 3=>4))
3 => 4

julia> rand((2, 3))
3

julia> rand(Float64, (2, 3))
2×3 Array{Float64,2}:
 0.999717  0.0143835  0.540787
 0.696556  0.783855   0.938235
```

!!! note
    `rand(rng, s::Union{AbstractDict,AbstractSet})`'nin karmaşıklığı `s`'nin uzunluğuna bağlı olarak lineerdir, eğer sabit karmaşıklıkta optimize edilmiş bir yöntem mevcut değilse, bu durum `Dict`, `Set` ve yoğun `BitSet`'ler için geçerlidir. Birkaç çağrıdan fazlası için, bunun yerine `rand(rng, collect(s))` kullanın veya uygun olduğunda `rand(rng, Dict(s))` veya `rand(rng, Set(s))` kullanın.

