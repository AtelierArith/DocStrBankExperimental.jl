```
*(s::Union{AbstractString, AbstractChar}, t::Union{AbstractString, AbstractChar}...) -> AbstractString
```

Dizeleri ve/veya karakterleri birleştirir, uygun şekilde bir [`String`](@ref) veya [`AnnotatedString`](@ref) üretir. Bu, argümanlar üzerinde [`string`](@ref) veya [`annotatedstring`](@ref) fonksiyonunu çağırmakla eşdeğerdir. Yerleşik dize türlerinin birleştirilmesi her zaman `String` türünde bir değer üretirken, diğer dize türleri uygun olduğunda farklı bir türde dize döndürmeyi seçebilir.

# Örnekler

```jldoctest
julia> "Hello " * "world"
"Hello world"

julia> 'j' * "ulia"
"julia"
```
