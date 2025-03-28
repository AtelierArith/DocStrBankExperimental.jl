```
setcpuaffinity(original_command::Cmd, cpus) -> command::Cmd
```

Establece la afinidad de CPU del `command` mediante una lista de IDs de CPU (basados en 1) `cpus`. Pasar `cpus = nothing` significa desactivar la afinidad de CPU si el `original_command` tiene alguna.

Esta función es compatible solo en Linux y Windows. No es compatible en macOS porque libuv no admite la configuración de afinidad.

!!! compat "Julia 1.8"
    Esta función requiere al menos Julia 1.8.


# Ejemplos

En Linux, se puede usar el programa de línea de comandos `taskset` para ver cómo funciona `setcpuaffinity`.

```julia
julia> run(setcpuaffinity(`sh -c 'taskset -p $$'`, [1, 2, 5]));
pid 2273's current affinity mask: 13
```

Tenga en cuenta que el valor de la máscara `13` refleja que los primeros, segundos y quintos bits (contando desde la posición menos significativa) están activados:

```julia
julia> 0b010011
0x13
```
