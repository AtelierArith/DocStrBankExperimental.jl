```
reinterpret(T::DataType, A::AbstractArray)
```

Construye una vista del arreglo con los mismos datos binarios que el arreglo dado, pero con `T` como tipo de elemento.

Esta función también funciona en arreglos "perezosos" cuyos elementos no se calculan hasta que se recuperan explícitamente. Por ejemplo, `reinterpret` en el rango `1:6` funciona de manera similar al vector denso `collect(1:6)`:

```jldoctest
julia> reinterpret(Float32, UInt32[1 2 3 4 5])
1×5 reinterpret(Float32, ::Matrix{UInt32}):
 1.0f-45  3.0f-45  4.0f-45  6.0f-45  7.0f-45

julia> reinterpret(Complex{Int}, 1:6)
3-element reinterpret(Complex{Int64}, ::UnitRange{Int64}):
 1 + 2im
 3 + 4im
 5 + 6im
```

Si la ubicación de los bits de relleno no se alinea entre `T` y `eltype(A)`, el arreglo resultante será de solo lectura o solo escritura, para evitar que se escriban o lean bits inválidos, respectivamente.

```jldoctest
julia> a = reinterpret(Tuple{UInt8, UInt32}, UInt32[1, 2])
1-element reinterpret(Tuple{UInt8, UInt32}, ::Vector{UInt32}):
 (0x01, 0x00000002)

julia> a[1] = 3
ERROR: El relleno del tipo Tuple{UInt8, UInt32} no es compatible con el tipo UInt32.

julia> b = reinterpret(UInt32, Tuple{UInt8, UInt32}[(0x01, 0x00000002)]); # mostrar dará error

julia> b[1]
ERROR: El relleno del tipo UInt32 no es compatible con el tipo Tuple{UInt8, UInt32}.
```
