```
crc32c(data, crc::UInt32=0x00000000)
```

Calcula el checksum CRC-32c de los datos dados, que pueden ser un `Array{UInt8}`, un subarreglo contiguo de este, o un `String`. Opcionalmente, puedes pasar un entero `crc` inicial para mezclarlo con el checksum. El parámetro `crc` se puede usar para calcular un checksum en datos divididos en fragmentos: realizar `crc32c(data2, crc32c(data1))` es equivalente al checksum de `[data1; data2]`. (Técnicamente, se calcula un checksum en orden little-endian).

También hay un método `crc32c(io, nb, crc)` para calcular el checksum de `nb` bytes de un flujo `io`, o `crc32c(io, crc)` para calcular el checksum de todos los bytes restantes. Por lo tanto, puedes hacer [`open(crc32c, filename)`](@ref) para calcular el checksum de un archivo completo, o `crc32c(seekstart(buf))` para calcular el checksum de un [`IOBuffer`](@ref) sin llamar a [`take!`](@ref).

Para un `String`, ten en cuenta que el resultado es específico de la codificación UTF-8 (se obtendría un checksum diferente de una codificación Unicode diferente). Para calcular el checksum de un `a::Array` de algún otro tipo de bits, puedes hacer `crc32c(reinterpret(UInt8,a))`, pero ten en cuenta que el resultado puede depender del orden de bytes.
