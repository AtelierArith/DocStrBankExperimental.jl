```
Iterators.filter(flt, itr)
```

Dada una función de predicado `flt` y un objeto iterable `itr`, devuelve un objeto iterable que al iterar produce los elementos `x` de `itr` que satisfacen `flt(x)`. El orden del iterador original se preserva.

Esta función es *perezosa*; es decir, se garantiza que devolverá en $Θ(1)$ tiempo y usará $Θ(1)$ espacio adicional, y `flt` no será llamada por una invocación de `filter`. Las llamadas a `flt` se realizarán al iterar sobre el objeto iterable devuelto. Estas llamadas no se almacenan en caché y se realizarán llamadas repetidas al reiterar.

!!! warning
    Transformaciones *perezosas* subsiguientes en el iterador devuelto por `filter`, como las realizadas por `Iterators.reverse` o `cycle`, también retrasarán las llamadas a `flt` hasta que se recojan o se itere sobre el objeto iterable devuelto. Si el predicado de filtro es no determinista o sus valores de retorno dependen del orden de iteración sobre los elementos de `itr`, la composición con transformaciones perezosas puede resultar en un comportamiento sorprendente. Si esto es indeseable, asegúrate de que `flt` sea una función pura o recoge iteradores intermedios de `filter` antes de realizar más transformaciones.


Consulta [`Base.filter`](@ref) para una implementación ansiosa de filtrado para arreglos.

# Ejemplos

```jldoctest
julia> f = Iterators.filter(isodd, [1, 2, 3, 4, 5])
Base.Iterators.Filter{typeof(isodd), Vector{Int64}}(isodd, [1, 2, 3, 4, 5])

julia> foreach(println, f)
1
3
5

julia> [x for x in [1, 2, 3, 4, 5] if isodd(x)]  # recoge un generador sobre Iterators.filter
Vector{Int64} de 3 elementos:
 1
 3
 5
```
