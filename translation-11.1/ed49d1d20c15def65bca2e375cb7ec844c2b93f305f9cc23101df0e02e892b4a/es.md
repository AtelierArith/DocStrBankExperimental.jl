```
insorted(x, v; by=identity, lt=isless, rev=false) -> Bool
```

Determina si un vector `v` contiene algún valor equivalente a `x`. El vector `v` debe estar ordenado de acuerdo con el orden definido por las palabras clave. Consulta [`sort!`](@ref) para el significado de las palabras clave y la definición de equivalencia. Ten en cuenta que la función `by` se aplica al valor buscado `x` así como a los valores en `v`.

La verificación se realiza generalmente utilizando búsqueda binaria, pero hay implementaciones optimizadas para algunas entradas.

Consulta también [`in`](@ref).

# Ejemplos

```jldoctest
julia> insorted(4, [1, 2, 4, 5, 5, 7]) # coincidencia única
true

julia> insorted(5, [1, 2, 4, 5, 5, 7]) # coincidencias múltiples
true

julia> insorted(3, [1, 2, 4, 5, 5, 7]) # sin coincidencia
false

julia> insorted(9, [1, 2, 4, 5, 5, 7]) # sin coincidencia
false

julia> insorted(0, [1, 2, 4, 5, 5, 7]) # sin coincidencia
false

julia> insorted(2=>"TWO", [1=>"one", 2=>"two", 4=>"four"], by=first) # compara las claves de los pares
true
```

!!! compat "Julia 1.6"
    `insorted` se agregó en Julia 1.6.

