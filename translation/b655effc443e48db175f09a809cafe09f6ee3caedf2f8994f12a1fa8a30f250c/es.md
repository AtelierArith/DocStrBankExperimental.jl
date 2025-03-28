```
LOAD_PATH
```

Un array de rutas para las declaraciones `using` e `import` a considerar como entornos de proyecto o directorios de paquetes al cargar código. Se llena en función de la variable de entorno [`JULIA_LOAD_PATH`](@ref JULIA_LOAD_PATH) si está configurada; de lo contrario, se establece por defecto en `["@", "@v#.#", "@stdlib"]`. Las entradas que comienzan con `@` tienen significados especiales:

  * `@` se refiere al "entorno activo actual", cuyo valor inicial se determina inicialmente por la variable de entorno [`JULIA_PROJECT`](@ref JULIA_PROJECT) o la opción de línea de comandos `--project`.
  * `@stdlib` se expande a la ruta absoluta del directorio de la biblioteca estándar de la instalación actual de Julia.
  * `@name` se refiere a un entorno nombrado, que se almacena en depósitos (ver [`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH)) bajo el subdirectorio `environments`. Los entornos nombrados del usuario se almacenan en `~/.julia/environments`, por lo que `@name` se referiría al entorno en `~/.julia/environments/name` si existe y contiene un archivo `Project.toml`. Si `name` contiene caracteres `#`, entonces se reemplazan por los componentes mayor, menor y de parche del número de versión de Julia. Por ejemplo, si estás ejecutando Julia 1.2, entonces `@v#.#` se expande a `@v1.2` y buscará un entorno con ese nombre, típicamente en `~/.julia/environments/v1.2`.

El valor completamente expandido de `LOAD_PATH` que se busca para proyectos y paquetes se puede ver llamando a la función `Base.load_path()`.

Ver también [`JULIA_LOAD_PATH`](@ref JULIA_LOAD_PATH), [`JULIA_PROJECT`](@ref JULIA_PROJECT), [`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH), y [Carga de Código](@ref code-loading).
