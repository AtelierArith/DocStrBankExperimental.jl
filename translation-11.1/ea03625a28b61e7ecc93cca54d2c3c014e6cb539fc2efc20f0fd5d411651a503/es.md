```
addprocs(machines; tunnel=false, sshflags=``, max_parallel=10, kwargs...) -> Lista de identificadores de procesos
```

Agrega procesos de trabajo en máquinas remotas a través de SSH. La configuración se realiza con argumentos de palabra clave (ver más abajo). En particular, se puede usar la palabra clave `exename` para especificar la ruta al binario `julia` en la(s) máquina(s) remota(s).

`machines` es un vector de "especificaciones de máquina" que se dan como cadenas en la forma `[user@]host[:port] [bind_addr[:port]]`. `user` se establece de forma predeterminada como el usuario actual y `port` como el puerto SSH estándar. Si se especifica `[bind_addr[:port]]`, otros trabajadores se conectarán a este trabajador en el `bind_addr` y `port` especificados.

Es posible lanzar múltiples procesos en un host remoto utilizando una tupla en el vector `machines` o la forma `(machine_spec, count)`, donde `count` es el número de trabajadores que se lanzarán en el host especificado. Pasar `:auto` como el conteo de trabajadores lanzará tantos trabajadores como el número de hilos de CPU en el host remoto.

**Ejemplos**:

```julia
addprocs([
    "remote1",               # un trabajador en 'remote1' iniciando sesión con el nombre de usuario actual
    "user@remote2",          # un trabajador en 'remote2' iniciando sesión con el nombre de usuario 'user'
    "user@remote3:2222",     # especificando el puerto SSH a '2222' para 'remote3'
    ("user@remote4", 4),     # lanzar 4 trabajadores en 'remote4'
    ("user@remote5", :auto), # lanzar tantos trabajadores como hilos de CPU en 'remote5'
])
```

**Argumentos de palabra clave**:

  * `tunnel`: si `true`, se utilizará un túnel SSH para conectarse al trabajador desde el proceso maestro. El valor predeterminado es `false`.
  * `multiplex`: si `true`, se utiliza multiplexión SSH para el túnel SSH. El valor predeterminado es `false`.
  * `ssh`: el nombre o la ruta del ejecutable del cliente SSH utilizado para iniciar los trabajadores. El valor predeterminado es `"ssh"`.
  * `sshflags`: especifica opciones ssh adicionales, p. ej. ```sshflags=`-i /home/foo/bar.pem` ```
  * `max_parallel`: especifica el número máximo de trabajadores conectados en paralelo en un host. El valor predeterminado es 10.
  * `shell`: especifica el tipo de shell al que ssh se conecta en los trabajadores.

      * `shell=:posix`: un shell Unix/Linux compatible con POSIX (sh, ksh, bash, dash, zsh, etc.). El valor predeterminado.
      * `shell=:csh`: un shell C de Unix (csh, tcsh).
      * `shell=:wincmd`: Microsoft Windows `cmd.exe`.
  * `dir`: especifica el directorio de trabajo en los trabajadores. El valor predeterminado es el directorio actual del host (como se encuentra con `pwd()`)
  * `enable_threaded_blas`: si `true`, entonces BLAS se ejecutará en múltiples hilos en los procesos añadidos. El valor predeterminado es `false`.
  * `exename`: nombre del ejecutable `julia`. El valor predeterminado es `"$(Sys.BINDIR)/julia"` o `"$(Sys.BINDIR)/julia-debug"` según sea el caso. Se recomienda que se use una versión común de Julia en todas las máquinas remotas porque la serialización y la distribución de código podrían fallar de lo contrario.
  * `exeflags`: banderas adicionales pasadas a los procesos de trabajo.
  * `topology`: Especifica cómo los trabajadores se conectan entre sí. Enviar un mensaje entre trabajadores no conectados resulta en un error.

      * `topology=:all_to_all`: Todos los procesos están conectados entre sí. El valor predeterminado.
      * `topology=:master_worker`: Solo el proceso controlador, es decir, `pid` 1 se conecta a los trabajadores. Los trabajadores no se conectan entre sí.
      * `topology=:custom`: El método `launch` del administrador de clústeres especifica la topología de conexión a través de los campos `ident` y `connect_idents` en `WorkerConfig`. Un trabajador con una identidad de administrador de clúster `ident` se conectará a todos los trabajadores especificados en `connect_idents`.
  * `lazy`: Aplicable solo con `topology=:all_to_all`. Si `true`, las conexiones trabajador-trabajador se configuran de manera perezosa, es decir, se configuran en la primera instancia de una llamada remota entre trabajadores. El valor predeterminado es true.
  * `env`: proporciona un array de pares de cadenas como `env=["JULIA_DEPOT_PATH"=>"/depot"]` para solicitar que se establezcan variables de entorno en la máquina remota. Por defecto, solo la variable de entorno `JULIA_WORKER_TIMEOUT` se pasa automáticamente del entorno local al remoto.
  * `cmdline_cookie`: pasa la cookie de autenticación a través de la opción de línea de comandos `--worker`. El comportamiento predeterminado (más seguro) de pasar la cookie a través de ssh stdio puede colgarse con trabajadores de Windows que utilizan versiones anteriores de Julia o Windows (pre-ConPTY), en cuyo caso `cmdline_cookie=true` ofrece una solución alternativa.

!!! compat "Julia 1.6"
    Los argumentos de palabra clave `ssh`, `shell`, `env` y `cmdline_cookie` se añadieron en Julia 1.6.


Variables de entorno:

Si el proceso maestro no logra establecer una conexión con un trabajador recién lanzado dentro de 60.0 segundos, el trabajador lo considera una situación fatal y termina. Este tiempo de espera se puede controlar a través de la variable de entorno `JULIA_WORKER_TIMEOUT`. El valor de `JULIA_WORKER_TIMEOUT` en el proceso maestro especifica el número de segundos que un trabajador recién lanzado espera para establecer la conexión.
