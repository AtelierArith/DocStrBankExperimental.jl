```
addprocs(np::Integer=Sys.CPU_THREADS; restrict=true, kwargs...) -> Lista de identificadores de procesos
```

Lanza `np` trabajadores en el host local utilizando el `LocalManager` incorporado.

Los trabajadores locales heredan el entorno de paquetes actual (es decir, proyecto activo, [`LOAD_PATH`](@ref) y [`DEPOT_PATH`](@ref)) del proceso principal.

!!! warning
    Tenga en cuenta que los trabajadores no ejecutan un script de inicio `~/.julia/config/startup.jl`, ni sincronizan su estado global (como opciones de línea de comandos, variables globales, definiciones de nuevos métodos y módulos cargados) con ninguno de los otros procesos en ejecución.


**Argumentos clave**:

  * `restrict::Bool`: si es `true` (por defecto) la vinculación está restringida a `127.0.0.1`.
  * `dir`, `exename`, `exeflags`, `env`, `topology`, `lazy`, `enable_threaded_blas`: mismo efecto que para `SSHManager`, consulte la documentación para [`addprocs(machines::AbstractVector)`](@ref).

!!! compat "Julia 1.9"
    La herencia del entorno de paquetes y el argumento clave `env` se añadieron en Julia 1.9.

