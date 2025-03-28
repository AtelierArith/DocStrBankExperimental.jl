```
DEPOT_PATH
```

Una pila de ubicaciones de "depósito" donde el administrador de paquetes, así como los mecanismos de carga de código de Julia, buscan registros de paquetes, paquetes instalados, entornos nombrados, clones de repositorios, imágenes de paquetes compilados en caché y archivos de configuración. Por defecto, incluye:

1. `~/.julia` donde `~` es el directorio de inicio del usuario según corresponda en el sistema;
2. un directorio del sistema compartido específico de la arquitectura, por ejemplo, `/usr/local/share/julia`;
3. un directorio del sistema compartido independiente de la arquitectura, por ejemplo, `/usr/share/julia`.

Así que `DEPOT_PATH` podría ser:

```julia
[joinpath(homedir(), ".julia"), "/usr/local/share/julia", "/usr/share/julia"]
```

La primera entrada es el "depósito del usuario" y debe ser escribible y propiedad del usuario actual. El depósito del usuario es donde: se clonan los registros, se instalan nuevas versiones de paquetes, se crean y actualizan entornos nombrados, se clonan repositorios de paquetes, se guardan archivos de imagen de paquetes recién compilados, se escriben archivos de registro, se revisan paquetes de desarrollo por defecto y se guarda la configuración global. Las entradas posteriores en la ruta del depósito se tratan como de solo lectura y son apropiadas para registros, paquetes, etc. instalados y gestionados por administradores del sistema.

`DEPOT_PATH` se llena en función de la variable de entorno [`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH) si está configurada.

## Contenidos de DEPOT_PATH

Cada entrada en `DEPOT_PATH` es una ruta a un directorio que contiene subdirectorios utilizados por Julia para diversos propósitos. Aquí hay un resumen de algunos de los subdirectorios que pueden existir en un depósito:

  * `artifacts`: Contiene contenido que los paquetes utilizan para el cual Pkg gestiona la instalación.
  * `clones`: Contiene clones completos de repositorios de paquetes. Mantenido por `Pkg.jl` y utilizado como caché.
  * `config`: Contiene configuración a nivel de julia, como un `startup.jl`
  * `compiled`: Contiene archivos precompilados `*.ji` para paquetes. Mantenido por Julia.
  * `dev`: Directorio predeterminado para `Pkg.develop`. Mantenido por `Pkg.jl` y el usuario.
  * `environments`: Entornos de paquetes predeterminados. Por ejemplo, el entorno global para una versión específica de julia. Mantenido por `Pkg.jl`.
  * `logs`: Contiene registros de operaciones de `Pkg` y `REPL`. Mantenido por `Pkg.jl` y `Julia`.
  * `packages`: Contiene paquetes, algunos de los cuales fueron instalados explícitamente y otros que son dependencias implícitas. Mantenido por `Pkg.jl`.
  * `registries`: Contiene registros de paquetes. Por defecto, solo `General`. Mantenido por `Pkg.jl`.
  * `scratchspaces`: Contiene contenido que un paquete instala a través del paquete [`Scratch.jl`](https://github.com/JuliaPackaging/Scratch.jl). `Pkg.gc()` eliminará contenido que se sabe que no se utiliza.

!!! nota
    Los paquetes que desean almacenar contenido deben usar el subdirectorio `scratchspaces` a través de [`Scratch.jl`](https://github.com/JuliaPackaging/Scratch.jl) en lugar de crear nuevos subdirectorios en la raíz del depósito.


Véase también [`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH), y [Carga de Código](@ref code-loading).
