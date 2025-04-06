```
hex2bytes!(dest::AbstractVector{UInt8}, itr)
```

Convierte un iterable `itr` de bytes que representan una cadena hexadecimal a su representación binaria, similar a [`hex2bytes`](@ref) excepto que la salida se escribe en su lugar en `dest`. La longitud de `dest` debe ser la mitad de la longitud de `itr`.

!!! compat "Julia 1.7"
    Llamar a hex2bytes! con iteradores que producen UInt8 requiere la versión 1.7. En versiones anteriores, puedes recolectar el iterable antes de llamar en su lugar.

