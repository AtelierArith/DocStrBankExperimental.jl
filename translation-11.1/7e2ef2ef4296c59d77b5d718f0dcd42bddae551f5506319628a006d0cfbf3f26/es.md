```
codeunits(s::AbstractString)
```

Obtiene un objeto similar a un vector que contiene las unidades de código de una cadena. Devuelve un envoltorio `CodeUnits` por defecto, pero `codeunits` puede definirse opcionalmente para nuevos tipos de cadena si es necesario.

# Ejemplos

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
