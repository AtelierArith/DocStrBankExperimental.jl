```
pointer_from_objref(x)
```

Obtiene la dirección de memoria de un objeto de Julia como un `Ptr`. La existencia del `Ptr` resultante no protegerá al objeto de la recolección de basura, por lo que debes asegurarte de que el objeto permanezca referenciado durante todo el tiempo que se utilizará el `Ptr`.

Esta función no se puede llamar en objetos inmutables, ya que no tienen direcciones de memoria estables.

Véase también [`unsafe_pointer_to_objref`](@ref).
