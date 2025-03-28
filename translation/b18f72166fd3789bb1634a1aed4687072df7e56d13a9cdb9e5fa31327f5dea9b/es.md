```
range(inicio, fin, longitud)
range(inicio, fin; longitud, paso)
range(inicio; longitud, fin, paso)
range(;inicio, longitud, fin, paso)
```

Construye un arreglo especializado con elementos espaciados uniformemente y almacenamiento optimizado (un [`AbstractRange`](@ref)) a partir de los argumentos. Matemáticamente, un rango está determinado de manera única por cualquiera de los tres `inicio`, `paso`, `fin` y `longitud`. Las invocaciones válidas de range son:

  * Llamar a `range` con cualquiera de los tres `inicio`, `paso`, `fin`, `longitud`.
  * Llamar a `range` con dos de `inicio`, `fin`, `longitud`. En este caso, se asumirá que `paso` es uno. Si ambos argumentos son enteros, se devolverá un [`UnitRange`](@ref).
  * Llamar a `range` con uno de `fin` o `longitud`. Se asumirá que `inicio` y `paso` son uno.

Consulta Ayuda Extendida para más detalles sobre el tipo devuelto. También consulta [`logrange`](@ref) para puntos espaciados logarítmicamente.

# Ejemplos

```jldoctest
julia> range(1, longitud=100)
1:100

julia> range(1, fin=100)
1:100

julia> range(1, paso=5, longitud=100)
1:5:496

julia> range(1, paso=5, fin=100)
1:5:96

julia> range(1, 10, longitud=101)
1.0:0.09:10.0

julia> range(1, 100, paso=5)
1:5:96

julia> range(fin=10, longitud=5)
6:10

julia> range(fin=10, paso=1, longitud=5)
6:1:10

julia> range(inicio=1, paso=1, fin=10)
1:1:10

julia> range(; longitud = 10)
Base.OneTo(10)

julia> range(; fin = 6)
Base.OneTo(6)

julia> range(; fin = 6.5)
1.0:1.0:6.0
```

Si `longitud` no se especifica y `fin - inicio` no es un múltiplo entero de `paso`, se producirá un rango que termina antes de `fin`.

```jldoctest
julia> range(1, 3.5, paso=2)
1.0:2.0:3.0
```

Se toma un cuidado especial para asegurar que los valores intermedios se calculen de manera racional. Para evitar esta sobrecarga inducida, consulta el constructor [`LinRange`](@ref).

!!! compat "Julia 1.1"
    `fin` como un argumento posicional requiere al menos Julia 1.1.


!!! compat "Julia 1.7"
    Las versiones sin argumentos de palabra clave y `inicio` como un argumento de palabra clave requieren al menos Julia 1.7.


!!! compat "Julia 1.8"
    Las versiones con `fin` como un único argumento de palabra clave, o `longitud` como un único argumento de palabra clave requieren al menos Julia 1.8.


# Ayuda Extendida

`range` producirá un `Base.OneTo` cuando los argumentos sean enteros y

  * Solo se proporciona `longitud`
  * Solo se proporciona `fin`

`range` producirá un `UnitRange` cuando los argumentos sean enteros y

  * Solo se proporcionan `inicio` y `fin`
  * Solo se proporcionan `longitud` y `fin`

No se produce un `UnitRange` si se proporciona `paso`, incluso si se especifica como uno.
