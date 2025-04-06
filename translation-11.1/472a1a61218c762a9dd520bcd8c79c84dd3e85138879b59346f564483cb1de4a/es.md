```
require(into::Module, module::Symbol)
```

Esta función es parte de la implementación de [`using`](@ref) / [`import`](@ref), si un módulo no está ya definido en `Main`. También se puede llamar directamente para forzar la recarga de un módulo, independientemente de si se ha cargado antes (por ejemplo, al desarrollar bibliotecas de forma interactiva).

Carga un archivo fuente, en el contexto del módulo `Main`, en cada nodo activo, buscando en ubicaciones estándar para archivos. `require` se considera una operación de nivel superior, por lo que establece la ruta de `include` actual pero no la utiliza para buscar archivos (ver ayuda para [`include`](@ref)). Esta función se utiliza típicamente para cargar código de biblioteca y es llamada implícitamente por `using` para cargar paquetes.

Al buscar archivos, `require` primero busca código de paquete en el arreglo global [`LOAD_PATH`](@ref). `require` es sensible a mayúsculas y minúsculas en todas las plataformas, incluidas aquellas con sistemas de archivos que no distinguen entre mayúsculas y minúsculas, como macOS y Windows.

Para más detalles sobre la carga de código, consulta las secciones del manual sobre [módulos](@ref modules) y [computación paralela](@ref code-availability).
