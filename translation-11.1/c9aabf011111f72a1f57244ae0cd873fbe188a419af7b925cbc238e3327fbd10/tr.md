```
eachrsplit(str::AbstractString, dlm; limit::Integer=0, keepempty::Bool=true)
eachrsplit(str::AbstractString; limit::Integer=0, keepempty::Bool=false)
```

`str` üzerinde `dlm` ayırıcı(ları) ile bölündüğünde üretilen `SubString`'lerin bir iteratörünü döndürür ve bunları ters sırayla (sağdan sola) verir. `dlm`, [`findprev`](@ref) fonksiyonunun ilk argümanı olarak izin verilen herhangi bir formatta (yani bir dize, tek bir karakter veya bir fonksiyon) veya bir karakter koleksiyonu olabilir.

`dlm` belirtilmezse, varsayılan olarak [`isspace`](@ref) kullanılır ve `keepempty` varsayılan olarak `false` olur.

İsteğe bağlı anahtar kelime argümanları şunlardır:

  * Eğer `limit > 0` ise, iteratör en fazla `limit - 1` kez bölme yapacak ve geri kalan dizeyi bölmeden döndürecektir. `limit < 1` bölmelere herhangi bir sınır koymaz (varsayılan).
  * `keepempty`: iterasyon sırasında boş alanların döndürülüp döndürülmeyeceği. Varsayılan, `dlm` argümanı olmadan `false`, `dlm` argümanı ile `true`'dur.

[`split`](@ref), [`rsplit`](@ref) ve [`eachsplit`](@ref) ile karşılaştırıldığında, bu fonksiyon girişteki alt dizeleri sağdan sola doğru iterasyon yapar.

Ayrıca bkz. [`eachsplit`](@ref), [`rsplit`](@ref).

!!! compat "Julia 1.11"
    Bu fonksiyon Julia 1.11 veya daha yenisini gerektirir.


# Örnekler

```jldoctest
julia> a = "Ma.r.ch";

julia> collect(eachrsplit(a, ".")) == ["ch", "r", "Ma"]
true

julia> collect(eachrsplit(a, "."; limit=2)) == ["ch", "Ma.r"]
true
```
