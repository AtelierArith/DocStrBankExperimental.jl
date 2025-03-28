```
cumsum(A; dims::Integer)
```

Suma acumulativa a lo largo de la dimensión `dims`. Véase también [`cumsum!`](@ref) para usar un array de salida preasignado, tanto por rendimiento como para controlar la precisión de la salida (por ejemplo, para evitar desbordamientos).

# Ejemplos

```jldoctest
julia> a = [1 2 3; 4 5 6]
2×3 Matrix{Int64}:
 1  2  3
 4  5  6

julia> cumsum(a, dims=1)
2×3 Matrix{Int64}:
 1  2  3
 5  7  9

julia> cumsum(a, dims=2)
2×3 Matrix{Int64}:
 1  3   6
 4  9  15
```

!!! nota
    El `eltype` del array de retorno es `Int` para enteros con signo de menos del tamaño de palabra del sistema y `UInt` para enteros sin signo de menos del tamaño de palabra del sistema. Para preservar el `eltype` de arrays con enteros pequeños con o sin signo, se debe usar `accumulate(+, A)`.

    ```jldoctest
    julia> cumsum(Int8[100, 28])
    2-element Vector{Int64}:
     100
     128

    julia> accumulate(+,Int8[100, 28])
    2-element Vector{Int8}:
      100
     -128
    ```

    En el primer caso, los enteros se amplían al tamaño de palabra del sistema y, por lo tanto, el resultado es `Int64[100, 128]`. En el segundo caso, no ocurre tal ampliación y el desbordamiento de enteros resulta en `Int8[100, -128]`.

