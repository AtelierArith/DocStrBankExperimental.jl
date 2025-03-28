```
WorkerConfig
```

Tipo utilizado por [`ClusterManager`](@ref)s para controlar los trabajadores añadidos a sus clústeres. Algunos campos son utilizados por todos los administradores de clúster para acceder a un host:

  * `io` – la conexión utilizada para acceder al trabajador (un subtipo de `IO` o `Nothing`)
  * `host` – la dirección del host (ya sea un `String` o `Nothing`)
  * `port` – el puerto en el host utilizado para conectarse al trabajador (ya sea un `Int` o `Nothing`)

Algunos son utilizados por el administrador de clúster para añadir trabajadores a un host ya inicializado:

  * `count` – el número de trabajadores que se lanzarán en el host
  * `exename` – la ruta al ejecutable de Julia en el host, por defecto es `"$(Sys.BINDIR)/julia"` o `"$(Sys.BINDIR)/julia-debug"`
  * `exeflags` – banderas a utilizar al lanzar Julia de forma remota

El campo `userdata` se utiliza para almacenar información para cada trabajador por administradores externos.

Algunos campos son utilizados por `SSHManager` y administradores similares:

  * `tunnel` – `true` (usar túneles), `false` (no usar túneles), o [`nothing`](@ref) (usar el valor por defecto para el administrador)
  * `multiplex` – `true` (usar multiplexión SSH para túneles) o `false`
  * `forward` – la opción de reenvío utilizada para la opción `-L` de ssh
  * `bind_addr` – la dirección en el host remoto a la que enlazar
  * `sshflags` – banderas a utilizar al establecer la conexión SSH
  * `max_parallel` – el número máximo de trabajadores a los que conectarse en paralelo en el host

Algunos campos son utilizados tanto por `LocalManager`s como por `SSHManager`s:

  * `connect_at` – determina si esta es una llamada de configuración de trabajador a trabajador o de controlador a trabajador
  * `process` – el proceso que se conectará (generalmente el administrador asignará esto durante [`addprocs`](@ref))
  * `ospid` – el ID del proceso según el sistema operativo del host, utilizado para interrumpir procesos de trabajadores
  * `environ` – diccionario privado utilizado para almacenar información temporal por administradores Local/SSH
  * `ident` – trabajador tal como es identificado por el [`ClusterManager`](@ref)
  * `connect_idents` – lista de IDs de trabajadores a los que el trabajador debe conectarse si se utiliza una topología personalizada
  * `enable_threaded_blas` – `true`, `false`, o `nothing`, si se debe usar BLAS en hilos o no en los trabajadores
