```
transcode(T, src)
```

Convierte datos de cadena entre codificaciones Unicode. `src` es un `String` o un `Vector{UIntXX}` de unidades de código UTF-XX, donde `XX` es 8, 16 o 32. `T` indica la codificación del valor de retorno: `String` para devolver un `String` (codificado en UTF-8) o `UIntXX` para devolver un `Vector{UIntXX}` de datos UTF-`XX`. (El alias [`Cwchar_t`](@ref) también se puede usar como el tipo entero, para convertir cadenas `wchar_t*` utilizadas por bibliotecas externas de C.)

La función `transcode` tiene éxito siempre que los datos de entrada se puedan representar razonablemente en la codificación de destino; siempre tiene éxito para conversiones entre codificaciones UTF-XX, incluso para datos Unicode no válidos.

Actualmente, solo se admite la conversión de/a UTF-8.

# Ejemplos

```jldoctest
julia> str = "αβγ"
"αβγ"

julia> transcode(UInt16, str)
3-element Vector{UInt16}:
 0x03b1
 0x03b2
 0x03b3

julia> transcode(String, transcode(UInt16, str))
"αβγ"
```
