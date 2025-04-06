```
Unicode.normalize(s::AbstractString; keywords...)
Unicode.normalize(s::AbstractString, normalform::Symbol)
```

Dizeyi `s` normalleştir. Varsayılan olarak, kanonik bileşim (`compose=true`) Unicode sürüm stabilitesini sağlamadan gerçekleştirilir (`compat=false`), bu da mümkün olan en kısa eşdeğer dizeyi üretir ancak daha önceki Unicode sürümlerinde bulunmayan bileşim karakterlerini tanıtabilir.

Alternatif olarak, Unicode standardının dört "normal formundan" biri belirtilebilir: `normalform` `:NFC`, `:NFD`, `:NFKC` veya `:NFKD` olabilir. Normal formlar C (kanonik bileşim) ve D (kanonik ayrıştırma), aynı soyut dize için farklı görsel olarak özdeş temsilleri tek bir kanonik forma dönüştürür; form C daha kompakt bir yapıya sahiptir. Normal formlar KC ve KD ayrıca "uyumluluk eşdeğerlerini" kanonikleştirir: soyut olarak benzer ancak görsel olarak farklı karakterleri tek bir kanonik seçeneğe dönüştürür (örneğin, ligatürleri bireysel karakterlere genişletir), form KC daha kompakt bir yapıya sahiptir.

Alternatif olarak, `Unicode.normalize(s; keywords...)` çağrılarak daha ince kontrol ve ek dönüşümler elde edilebilir; burada aşağıdaki boolean anahtar kelime seçeneklerinden herhangi sayıda (hepsi `compose` dışında varsayılan olarak `false`'dur) belirtilir:

  * `compose=false`: kanonik bileşimi gerçekleştirme
  * `decompose=true`: kanonik bileşimin yerine kanonik ayrıştırma yap (`compose=true` mevcutsa göz ardı edilir)
  * `compat=true`: uyumluluk eşdeğerleri kanonikleştirilir
  * `casefold=true`: Unicode büyük/küçük harf katlama işlemi yap, örneğin büyük/küçük harf duyarsız dize karşılaştırması için
  * `newline2lf=true`, `newline2ls=true` veya `newline2ps=true`: çeşitli yeni satır dizilerini (LF, CRLF, CR, NEL) sırasıyla bir satır besleme (LF), satır ayırma (LS) veya paragraf ayırma (PS) karakterine dönüştür
  * `stripmark=true`: diakritik işaretleri (örneğin, aksanlar) kaldır
  * `stripignore=true`: Unicode'un "varsayılan yok sayılabilir" karakterlerini (örneğin, yumuşak tire veya soldan sağa işaret) kaldır
  * `stripcc=true`: kontrol karakterlerini kaldır; yatay sekmeler ve form beslemeleri boşluklara dönüştürülür; yeni satırlar da boşluklara dönüştürülür, aksi takdirde bir yeni satır dönüştürme bayrağı belirtilmedikçe
  * `rejectna=true`: atanmış kod noktaları bulunursa bir hata fırlat
  * `stable=true`: Unicode sürüm stabilitesini zorla (daha önceki Unicode sürümlerinden eksik karakterler tanıtma)

Ayrıca, `chartransform` anahtar kelimesini (varsayılan olarak `identity`) kullanarak `Integer` kod noktalarını kod noktalarına eşleyen keyfi bir *fonksiyon* geçirebilirsiniz; bu, `s` işlenirken her karakter üzerinde çağrılır ve keyfi ek normalizasyonlar gerçekleştirmek için kullanılır. Örneğin, `chartransform=Unicode.julia_chartransform` geçirerek, Julia'nın tanımlayıcıları ayrıştırırken gerçekleştirdiği birkaç Julia'ya özgü karakter normalizasyonunu uygulayabilirsiniz (NFC normalizasyonuna ek olarak: `compose=true, stable=true`).

Örneğin, NFKC `compose=true, compat=true, stable=true` seçeneklerine karşılık gelir.

# Örnekler

```jldoctest
julia> "é" == Unicode.normalize("é") #LHS: Unicode U+00e9, RHS: U+0065 & U+0301
true

julia> "μ" == Unicode.normalize("µ", compat=true) #LHS: Unicode U+03bc, RHS: Unicode U+00b5
true

julia> Unicode.normalize("JuLiA", casefold=true)
"julia"

julia> Unicode.normalize("JúLiA", stripmark=true)
"JuLiA"
```

!!! compat "Julia 1.8"
    `chartransform` anahtar kelime argümanı Julia 1.8 gerektirir.

