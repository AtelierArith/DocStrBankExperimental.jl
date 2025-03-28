```
searchsorted(v, x; by=identity, lt=isless, rev=false)
```

Devuelve el rango de índices en `v` donde los valores son equivalentes a `x`, o un rango vacío ubicado en el punto de inserción si `v` no contiene valores equivalentes a `x`. El vector `v` debe estar ordenado de acuerdo con el orden definido por las palabras clave. Consulta [`sort!`](@ref) para el significado de las palabras clave y la definición de equivalencia. Ten en cuenta que la función `by` se aplica al valor buscado `x` así como a los valores en `v`.

El rango se encuentra generalmente utilizando búsqueda binaria, pero hay implementaciones optimizadas para algunas entradas.

Consulta también: [`searchsortedfirst`](@ref), [`sort!`](@ref), [`insorted`](@ref), [`findall`](@ref).

# Ejemplos

```jldoctest
julia> searchsorted([1, 2, 4, 5, 5, 7], 4) # coincidencia única
3:3

julia> searchsorted([1, 2, 4, 5, 5, 7], 5) # coincidencias múltiples
4:5

julia> searchsorted([1, 2, 4, 5, 5, 7], 3) # sin coincidencia, insertar en el medio
3:2

julia> searchsorted([1, 2, 4, 5, 5, 7], 9) # sin coincidencia, insertar al final
7:6

julia> searchsorted([1, 2, 4, 5, 5, 7], 0) # sin coincidencia, insertar al inicio
1:0

julia> searchsorted([1=>"one", 2=>"two", 2=>"two", 4=>"four"], 2=>"two", by=first) # comparar las claves de los pares
2:3
```
