```
mergewith(combine, d::AbstractDict, others::AbstractDict...)
mergewith(combine)
merge(combine, d::AbstractDict, others::AbstractDict...)
```

Verilen koleksiyonlardan birleştirilmiş bir koleksiyon oluşturun. Gerekirse, sonuç koleksiyonunun türleri birleştirilen koleksiyonların türlerini karşılamak için yükseltilecektir. Aynı anahtara sahip değerler, birleştirici fonksiyon kullanılarak birleştirilecektir. Curry biçimi `mergewith(combine)` fonksiyonu `(args...) -> mergewith(combine, args...)` döndürür.

`merge(combine::Union{Function,Type}, args...)` metodu, geriye dönük uyumluluk için `mergewith(combine, args...)`'nin bir takma adı olarak hala mevcuttur.

!!! uyumluluk "Julia 1.5"
    `mergewith` Julia 1.5 veya daha yenisini gerektirir.


# Örnekler

```jldoctest
julia> a = Dict("foo" => 0.0, "bar" => 42.0)
Dict{String, Float64} with 2 entries:
  "bar" => 42.0
  "foo" => 0.0

julia> b = Dict("baz" => 17, "bar" => 4711)
Dict{String, Int64} with 2 entries:
  "bar" => 4711
  "baz" => 17

julia> mergewith(+, a, b)
Dict{String, Float64} with 3 entries:
  "bar" => 4753.0
  "baz" => 17.0
  "foo" => 0.0

julia> ans == mergewith(+)(a, b)
true
```
