```
IteratorEltype(itertype::Type) -> IteratorEltype
```

Dado el tipo de un iterador, devuelve uno de los siguientes valores:

  * `EltypeUnknown()` si el tipo de elementos producidos por el iterador no se conoce de antemano.
  * `HasEltype()` si el tipo de elemento es conocido, y [`eltype`](@ref) devolvería un valor significativo.

`HasEltype()` es el valor predeterminado, ya que se asume que los iteradores implementan [`eltype`](@ref).

Este rasgo se utiliza generalmente para seleccionar entre algoritmos que pre-asignan un tipo específico de resultado y algoritmos que eligen un tipo de resultado basado en los tipos de los valores producidos.

```jldoctest
julia> Base.IteratorEltype(1:5)
Base.HasEltype()
```
