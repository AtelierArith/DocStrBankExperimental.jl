```
codeunits(s::AbstractString)
```

Erhalten Sie ein vektorähnliches Objekt, das die Codeeinheiten eines Strings enthält. Gibt standardmäßig einen `CodeUnits`-Wrapper zurück, aber `codeunits` kann optional für neue String-Typen definiert werden, wenn dies erforderlich ist.

# Beispiele

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
