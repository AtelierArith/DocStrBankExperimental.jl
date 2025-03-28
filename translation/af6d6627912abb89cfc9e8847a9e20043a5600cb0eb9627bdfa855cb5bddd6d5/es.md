```
IteratorSize(itertype::Type) -> IteratorSize
```

Dado el tipo de un iterador, devuelve uno de los siguientes valores:

  * `SizeUnknown()` si la longitud (número de elementos) no se puede determinar de antemano.
  * `HasLength()` si hay una longitud fija y finita.
  * `HasShape{N}()` si hay una longitud conocida más una noción de forma multidimensional (como para un arreglo). En este caso, `N` debe indicar el número de dimensiones, y la función [`axes`](@ref) es válida para el iterador.
  * `IsInfinite()` si el iterador produce valores para siempre.

El valor predeterminado (para iteradores que no definen esta función) es `HasLength()`. Esto significa que se asume que la mayoría de los iteradores implementan [`length`](@ref).

Este rasgo se utiliza generalmente para seleccionar entre algoritmos que pre-asignan espacio para su resultado y algoritmos que redimensionan su resultado de manera incremental.

```jldoctest
julia> Base.IteratorSize(1:5)
Base.HasShape{1}()

julia> Base.IteratorSize((2,3))
Base.HasLength()
```
