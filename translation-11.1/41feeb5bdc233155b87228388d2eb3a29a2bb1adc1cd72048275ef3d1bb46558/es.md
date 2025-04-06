```
Iterators.reverse(itr)
```

Dado un iterador `itr`, entonces `reverse(itr)` es un iterador sobre la misma colección pero en el orden inverso. Este iterador es "perezoso" en el sentido de que no hace una copia de la colección para invertirla; consulta [`Base.reverse`](@ref) para una implementación ansiosa.

(Por defecto, esto devuelve un objeto `Iterators.Reverse` que envuelve `itr`, el cual es iterable si los métodos correspondientes [`iterate`](@ref) están definidos, pero algunos tipos de `itr` pueden implementar comportamientos más especializados de `Iterators.reverse`.)

No todos los tipos de iteradores `T` soportan la iteración en orden inverso. Si `T` no lo hace, entonces iterar sobre `Iterators.reverse(itr::T)` lanzará un [`MethodError`](@ref) debido a los métodos `iterate` faltantes para `Iterators.Reverse{T}`. (Para implementar estos métodos, el iterador original `itr::T` se puede obtener de un objeto `r::Iterators.Reverse{T}` mediante `r.itr`; más generalmente, se puede usar `Iterators.reverse(r)`.)

# Ejemplos

```jldoctest
julia> foreach(println, Iterators.reverse(1:5))
5
4
3
2
1
```
