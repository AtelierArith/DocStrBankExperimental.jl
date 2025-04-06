```
searchsortedfirst(v, x; by=identity, lt=isless, rev=false)
```

Devuelve el índice del primer valor en `v` que no está ordenado antes de `x`. Si todos los valores en `v` están ordenados antes de `x`, devuelve `lastindex(v) + 1`.

El vector `v` debe estar ordenado de acuerdo con el orden definido por las palabras clave. Insertar `x` en el índice devuelto mantendrá el orden ordenado. Consulta [`sort!`](@ref) para el significado y uso de las palabras clave. Ten en cuenta que la función `by` se aplica al valor buscado `x` así como a los valores en `v`.

El índice se encuentra generalmente utilizando búsqueda binaria, pero hay implementaciones optimizadas para algunas entradas.

Consulta también: [`searchsortedlast`](@ref), [`searchsorted`](@ref), [`findfirst`](@ref).

# Ejemplos

```jldoctest
julia> searchsortedfirst([1, 2, 4, 5, 5, 7], 4) # coincidencia única
3

julia> searchsortedfirst([1, 2, 4, 5, 5, 7], 5) # múltiples coincidencias
4

julia> searchsortedfirst([1, 2, 4, 5, 5, 7], 3) # sin coincidencia, insertar en el medio
3

julia> searchsortedfirst([1, 2, 4, 5, 5, 7], 9) # sin coincidencia, insertar al final
7

julia> searchsortedfirst([1, 2, 4, 5, 5, 7], 0) # sin coincidencia, insertar al inicio
1

julia> searchsortedfirst([1=>"one", 2=>"two", 4=>"four"], 3=>"three", by=first) # comparar las claves de los pares
3
```
