```
bytes2hex(itr) -> String
bytes2hex(io::IO, itr)
```

Convierte un iterador `itr` de bytes a su representación en cadena hexadecimal, ya sea devolviendo un `String` a través de `bytes2hex(itr)` o escribiendo la cadena en un flujo `io` a través de `bytes2hex(io, itr)`.  Los caracteres hexadecimales son todos en minúsculas.

!!! compat "Julia 1.7"
    Llamar a `bytes2hex` con iteradores arbitrarios que producen valores `UInt8` requiere Julia 1.7 o posterior. En versiones anteriores, puedes `collect` el iterador antes de llamar a `bytes2hex`.


# Ejemplos

```jldoctest
julia> a = string(12345, base = 16)
"3039"

julia> b = hex2bytes(a)
2-element Vector{UInt8}:
 0x30
 0x39

julia> bytes2hex(b)
"3039"
```
