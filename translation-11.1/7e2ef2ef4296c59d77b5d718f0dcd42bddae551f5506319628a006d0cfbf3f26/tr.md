```
codeunits(s::AbstractString)
```

Bir dize içindeki kod birimlerini içeren vektör benzeri bir nesne elde edin. Varsayılan olarak bir `CodeUnits` sarmalayıcı döner, ancak gerekirse yeni dize türleri için `codeunits` isteğe bağlı olarak tanımlanabilir.

# Örnekler

```jldoctest
julia> codeunits("Juλia")
6-element Base.CodeUnits{UInt8, String}:
 0x4a
 0x75
 0xce
 0xbb
 0x69
 0x61
```
