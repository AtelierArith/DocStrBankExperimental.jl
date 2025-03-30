```
BigFloat(x::Union{Real, AbstractString} [, rounding::RoundingMode=rounding(BigFloat)]; [precision::Integer=precision(BigFloat)])
```

`x`'den `precision` ile birlikte, keyfi hassasiyetli bir kayan nokta sayısı oluşturur. `rounding` argümanı, dönüşüm tam olarak yapılamazsa sonucun hangi yönde yuvarlanması gerektiğini belirtir. Sağlanmadığı takdirde, bunlar mevcut küresel değerler tarafından ayarlanır.

`BigFloat(x::Real)` `convert(BigFloat,x)` ile aynıdır, ancak `x` kendisi zaten `BigFloat` ise, bu durumda mevcut küresel hassasiyet ayarlarına sahip bir değer döndürür; `convert` her zaman `x`'i döndürecektir.

`BigFloat(x::AbstractString)` [`parse`](@ref) ile aynıdır. Bu, ondalık literallerin ayrıştırıldığında `Float64`'e dönüştürüldüğü için sağlanmıştır, bu nedenle `BigFloat(2.1)` beklediğiniz sonucu vermeyebilir.

Ayrıca bakınız:

  * [`@big_str`](@ref)
  * [`rounding`](@ref) ve [`setrounding`](@ref)
  * [`precision`](@ref) ve [`setprecision`](@ref)

!!! compat "Julia 1.1"
    `precision` bir anahtar argümanı olarak en az Julia 1.1 gerektirir. Julia 1.0'da `precision` ikinci konumsal argümandır (`BigFloat(x, precision)`).


# Örnekler

```jldoctest
julia> BigFloat(2.1) # 2.1 burada bir Float64
2.100000000000000088817841970012523233890533447265625

julia> BigFloat("2.1") # 2.1'e en yakın BigFloat
2.099999999999999999999999999999999999999999999999999999999999999999999999999986

julia> BigFloat("2.1", RoundUp)
2.100000000000000000000000000000000000000000000000000000000000000000000000000021

julia> BigFloat("2.1", RoundUp, precision=128)
2.100000000000000000000000000000000000007
```
