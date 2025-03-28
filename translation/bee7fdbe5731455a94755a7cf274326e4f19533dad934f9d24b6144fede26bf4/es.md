```
searchsortedlast(v, x; by=identity, lt=isless, rev=false)
```

Devuelve el índice del último valor en `v` que no está ordenado después de `x`. Si todos los valores en `v` están ordenados después de `x`, devuelve `firstindex(v) - 1`.

El vector `v` debe estar ordenado de acuerdo con el orden definido por las palabras clave. Insertar `x` inmediatamente después del índice devuelto mantendrá el orden ordenado. Consulta [`sort!`](@ref) para el significado y uso de las palabras clave. Ten en cuenta que la función `by` se aplica al valor buscado `x` así como a los valores en `v`.

El índice se encuentra generalmente utilizando búsqueda binaria, pero hay implementaciones optimizadas para algunas entradas.

# Ejemplos

```jldoctest
julia> searchsortedlast([1, 2, 4, 5, 5, 7], 4) # coincidencia única
3

julia> searchsortedlast([1, 2, 4, 5, 5, 7], 5) # múltiples coincidencias
5

julia> searchsortedlast([1, 2, 4, 5, 5, 7], 3) # sin coincidencia, insertar en el medio
2

julia> searchsortedlast([1, 2, 4, 5, 5, 7], 9) # sin coincidencia, insertar al final
6

julia> searchsortedlast([1, 2, 4, 5, 5, 7], 0) # sin coincidencia, insertar al inicio
0

julia> searchsortedlast([1=>"one", 2=>"two", 4=>"four"], 3=>"three", by=first) # comparar las claves de los pares
2
```
