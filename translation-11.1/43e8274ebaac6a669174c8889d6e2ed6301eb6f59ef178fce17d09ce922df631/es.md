```
AtomicMemory{T} == GenericMemory{:atomic, T, Core.CPU}
```

Vector denso de tamaño fijo [`DenseVector{T}`](@ref DenseVector). El acceso a cualquiera de sus elementos se realiza de manera atómica (con ordenamiento `:monotonic`). Establecer cualquiera de los elementos debe llevarse a cabo utilizando el macro `@atomic` y especificando explícitamente el ordenamiento.

!!! warning
    Cada elemento es atómico de manera independiente cuando se accede, y no se puede establecer de manera no atómica. Actualmente, el macro `@atomic` y la interfaz de nivel superior no se han completado, pero los bloques de construcción para una futura implementación son los intrínsecos internos `Core.memoryrefget`, `Core.memoryrefset!`, `Core.memoryref_isassigned`, `Core.memoryrefswap!`, `Core.memoryrefmodify!`, y `Core.memoryrefreplace!`.


Para más detalles, consulta [Operaciones Atómicas](@ref man-atomic-operations)

!!! compat "Julia 1.11"
    Este tipo requiere Julia 1.11 o posterior.

