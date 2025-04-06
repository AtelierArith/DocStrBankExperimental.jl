```
unsafe_pointer_to_objref(p::Ptr)
```

Convierte un `Ptr` a una referencia de objeto. Asume que el puntero se refiere a un objeto de Julia válido asignado en el heap. Si este no es el caso, resulta en un comportamiento indefinido, por lo que esta función se considera "insegura" y debe usarse con precaución.

Ver también [`pointer_from_objref`](@ref).
