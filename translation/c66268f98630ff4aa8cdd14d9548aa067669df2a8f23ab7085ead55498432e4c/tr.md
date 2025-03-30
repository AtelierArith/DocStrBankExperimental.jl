```
eachsplit(str::AbstractString, dlm; limit::Integer=0, keepempty::Bool=true)
eachsplit(str::AbstractString; limit::Integer=0, keepempty::Bool=false)
```

`str`'yi `dlm` ayırıcılarının bulunduğu yerlerde ayırın ve alt dizelerin üzerinde bir yineleyici döndürün. `dlm`, [`findnext`](@ref) fonksiyonunun ilk argümanı olarak izin verilen herhangi bir formatta (yani bir dize, düzenli ifade veya bir fonksiyon olarak) veya tek bir karakter ya da karakterler koleksiyonu olarak olabilir.

`dlm` belirtilmezse, varsayılan olarak [`isspace`](@ref) kullanılır.

İsteğe bağlı anahtar kelime argümanları şunlardır:

  * `limit`: sonucun maksimum boyutu. `limit=0` maksimum yoktur (varsayılan)
  * `keepempty`: boş alanların sonuçta tutulup tutulmayacağı. Varsayılan, `dlm` argümanı olmadan `false`, `dlm` argümanı ile `true`'dur.

Ayrıca bkz. [`split`](@ref).

!!! compat "Julia 1.8"
    `eachsplit` fonksiyonu en az Julia 1.8 gerektirir.


# Örnekler

```jldoctest
julia> a = "Ma.rch"
"Ma.rch"

julia> b = eachsplit(a, ".")
Base.SplitIterator{String, String}("Ma.rch", ".", 0, true)

julia> collect(b)
2-element Vector{SubString{String}}:
 "Ma"
 "rch"
```
