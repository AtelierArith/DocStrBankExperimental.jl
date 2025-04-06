```
split(str::AbstractString, dlm; limit::Integer=0, keepempty::Bool=true)
split(str::AbstractString; limit::Integer=0, keepempty::Bool=false)
```

`str`'yi `dlm` ayırıcılarının bulunduğu yerlerde alt dizeler dizisine ayırır. `dlm`, [`findnext`](@ref) fonksiyonunun ilk argümanı olarak izin verilen herhangi bir formatta (yani bir dize, düzenli ifade veya bir fonksiyon olarak) veya tek bir karakter ya da karakterler koleksiyonu olarak olabilir.

Eğer `dlm` belirtilmezse, varsayılan olarak [`isspace`](@ref) kullanılır.

İsteğe bağlı anahtar kelime argümanları şunlardır:

  * `limit`: sonucun maksimum boyutu. `limit=0` maksimum yoktur anlamına gelir (varsayılan)
  * `keepempty`: boş alanların sonuçta tutulup tutulmayacağı. Varsayılan, `dlm` argümanı olmadan `false`, `dlm` argümanı ile `true`'dur.

Ayrıca [`rsplit`](@ref), [`eachsplit`](@ref) ile de bakılabilir.

# Örnekler

```jldoctest
julia> a = "Ma.rch"
"Ma.rch"

julia> split(a, ".")
2-element Vector{SubString{String}}:
 "Ma"
 "rch"
```
