```
hex2bytes(itr)
```

Dado un iterable `itr` de códigos ASCII para una secuencia de dígitos hexadecimales, devuelve un `Vector{UInt8}` de bytes correspondientes a la representación binaria: cada par sucesivo de dígitos hexadecimales en `itr` da el valor de un byte en el vector de retorno.

La longitud de `itr` debe ser par, y el array devuelto tiene la mitad de la longitud de `itr`. Véase también [`hex2bytes!`](@ref) para una versión en su lugar, y [`bytes2hex`](@ref) para la inversa.

!!! compat "Julia 1.7"
    Llamar a `hex2bytes` con iteradores que producen valores `UInt8` requiere Julia 1.7 o posterior. En versiones anteriores, puedes `collect` el iterador antes de llamar a `hex2bytes`.


# Ejemplos

```jldoctest
julia> s = string(12345, base = 16)
"3039"

julia> hex2bytes(s)
2-element Vector{UInt8}:
 0x30
 0x39

julia> a = b"01abEF"
6-element Base.CodeUnits{UInt8, String}:
 0x30
 0x31
 0x61
 0x62
 0x45
 0x46

julia> hex2bytes(a)
3-element Vector{UInt8}:
 0x01
 0xab
 0xef
```
