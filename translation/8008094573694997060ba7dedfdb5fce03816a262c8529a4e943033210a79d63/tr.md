```
@deprecate eski yeni [export_eski=true]
```

`eski` metodunu depreke et ve `yeni` çağrısını belirt, bu süreçte belirtilen imzaya sahip yeni bir `eski` metodu tanımla.

`eski`nin dışa aktarılmasını önlemek için `export_eski`'yi `false` olarak ayarla.

Ayrıca [`Base.depwarn()`](@ref) bak.

!!! uyumluluk "Julia 1.5"
    Julia 1.5 itibarıyla, `@deprecate` ile tanımlanan fonksiyonlar, `julia` `--depwarn=yes` bayrağı olmadan çalıştırıldığında uyarı yazdırmaz, çünkü `--depwarn` seçeneğinin varsayılan değeri `hayır`dır. Uyarılar `Pkg.test()` tarafından çalıştırılan testlerden yazdırılır.


# Örnekler

```jldoctest
julia> @deprecate eski(x) yeni(x)
eski (1 metod içeren genel fonksiyon)

julia> @deprecate eski(x) yeni(x) false
eski (1 metod içeren genel fonksiyon)
```

Açık tür notları olmadan `@deprecate` çağrıları, `Any` türünde herhangi bir sayıda konumsal ve anahtar kelime argümanı kabul eden depreke edilmiş metodlar tanımlayacaktır.

!!! uyumluluk "Julia 1.9"
    Anahtar kelime argümanları, Julia 1.9 itibarıyla açık tür notu olmadığında iletilir. Daha eski sürümler için, konumsal ve anahtar kelime argümanlarını manuel olarak iletmek için `@deprecate eski(args...; kwargs...) yeni(args...; kwargs...)` yapabilirsiniz.


Deprekasyonu belirli bir imzaya kısıtlamak için, `eski`nin argümanlarını not edin. Örneğin,

```jldoctest; filter = r"@ .*"a
julia> yeni(x::Int) = x;

julia> yeni(x::Float64) = 2x;

julia> @deprecate eski(x::Int) yeni(x);

julia> methods(eski)
# Ana'dan "eski" genel fonksiyonu için 1 metod:
 [1] eski(x::Int64)
     @ deprecated.jl:94
```

`yeni(x::Int)` ile aynısını yansıtan `eski(x::Int)` metodunu tanımlayacak ve depreke edecek, ancak `yeni(x::Float64)` metodunu tanımlamayacak veya depreke etmeyecektir.
