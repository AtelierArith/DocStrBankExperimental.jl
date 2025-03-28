```
PipeBuffer(data::AbstractVector{UInt8}=UInt8[]; maxsize::Integer = typemax(Int))
```

Un [`IOBuffer`](@ref) que permite la lectura y realiza escrituras mediante la adición. No se admite la búsqueda ni la truncación. Consulte [`IOBuffer`](@ref) para los constructores disponibles. Si se proporciona `data`, crea un `PipeBuffer` para operar en un vector de datos, especificando opcionalmente un tamaño más allá del cual el `Array` subyacente no puede crecer.
