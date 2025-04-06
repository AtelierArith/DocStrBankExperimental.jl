```
memoryref(::GenericMemory, index::Integer)
memoryref(::GenericMemoryRef, index::Integer)
```

Construye un `GenericMemoryRef` a partir de un objeto de memoria y un índice de desplazamiento (basado en 1) que también puede ser negativo. Esto siempre devuelve un objeto dentro de los límites, y lanzará un error si eso no es posible (porque el índice resultaría en un desplazamiento fuera de los límites de la memoria subyacente).
