```
free(addr::Ptr)
```

Llama a `free` de la biblioteca estándar de C. Solo usa esto en memoria obtenida de [`malloc`](@ref), no en punteros recuperados de otras bibliotecas de C. Los objetos [`Ptr`](@ref) obtenidos de bibliotecas de C deben ser liberados por las funciones free definidas en esa biblioteca, para evitar fallos de aserción si existen múltiples bibliotecas `libc` en el sistema.
