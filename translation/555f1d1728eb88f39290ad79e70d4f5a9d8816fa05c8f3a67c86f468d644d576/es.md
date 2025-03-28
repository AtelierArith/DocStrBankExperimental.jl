# External Profiler Support

Julia proporciona soporte explícito para algunos perfiles de trazado externos, lo que te permite obtener una visión general del comportamiento de ejecución del tiempo de ejecución.

Los perfiles actualmente soportados son:

  * [Tracy](https://github.com/wolfpld/tracy)
  * [Intel VTune (ITTAPI)](https://github.com/intel/ittapi)

### Adding New Zones

Para agregar nuevas zonas, utiliza el macro `JL_TIMING`. Puedes encontrar numerosos ejemplos a lo largo del código buscando `JL_TIMING`. Para agregar un nuevo tipo de zona, lo añades a `JL_TIMING_OWNERS` (y posiblemente a `JL_TIMING_EVENTS`).

### Dynamically Enabling and Disabling Zones

La variable de entorno [`JULIA_TIMING_SUBSYSTEMS`](@ref JULIA_TIMING_SUBSYSTEMS) te permite habilitar o deshabilitar zonas para una ejecución específica de Julia. Por ejemplo, establecer la variable en `+GC,-INFERENCE` habilitará las zonas `GC` y deshabilitará las zonas `INFERENCE`.

## Tracy Profiler

[Tracy](https://github.com/wolfpld/tracy) es un perfilador flexible que se puede integrar opcionalmente con Julia.

Una sesión típica de Tracy podría verse así:

![Uso típico de Tracy](tracy.png)

### Building Julia with Tracy

Para habilitar la integración de Tracy, construye Julia con la opción adicional `WITH_TRACY=1` en el archivo `Make.user`.

### Installing the Tracy Profile Viewer

La forma más fácil de obtener el visor de perfil es agregando el paquete `TracyProfiler_jll` y lanzando el perfilador con:

```julia
run(TracyProfiler_jll.tracy())
```

!!! note
    En macOS, es posible que desees establecer la variable de entorno `TRACY_DPI_SCALE` en `1.0` si los elementos de la interfaz de usuario en el perfilador parecen excesivamente grandes.


Para ejecutar una instancia "sin cabeza" que guarde el rastro en el disco, usa

```julia
run(`$(TracyProfiler_jll.capture()) -o mytracefile.tracy`)
```

en su lugar.

Para obtener información sobre el uso de la interfaz de usuario de Tracy, consulta el manual de Tracy.

### Profiling Julia with Tracy

Un flujo de trabajo típico para perfilar Julia con Tracy implica iniciar Julia usando:

```julia
JULIA_WAIT_FOR_TRACY=1 ./julia -e '...'
```

La variable de entorno asegura que Julia espere hasta que se haya conectado exitosamente al perfilador Tracy antes de continuar con la ejecución. Después, usa la interfaz de usuario del perfilador Tracy, haz clic en `Conectar`, y la ejecución de Julia debería reanudarse y el perfilado debería comenzar.

### Profiling package precompilation with Tracy

Para perfilar el proceso de precompilación de un paquete, es más fácil llamar explícitamente a `Base.compilecache` con el paquete que deseas precompilar:

```julia
pkg = Base.identify_package("SparseArrays")
withenv("JULIA_WAIT_FOR_TRACY" => 1, "TRACY_PORT" => 9001) do
    Base.compilecache(pkg)
end
```

Aquí, usamos un puerto personalizado para Tracy, lo que facilita encontrar el cliente correcto en la interfaz de usuario de Tracy para conectarse.

### Adding metadata to zones

Las diversas funciones `jl_timing_show_*` y `jl_timing_printf` se pueden utilizar para adjuntar una cadena (o cadenas) a una zona. Por ejemplo, la zona de traza para la inferencia muestra la instancia del método que se está inferiendo.

La función `TracyCZoneColor` se puede utilizar para establecer el color de una zona determinada. Busca en el código para ver cómo se utiliza.

### Viewing Tracy files in your browser

Visita https://topolarity.github.io/trace-viewer/ para un visor web (experimental) para trazas de Tracy.

Puedes abrir un archivo local `.tracy` o proporcionar una URL de la web (por ejemplo, un archivo en un repositorio de Github). Si cargas un archivo de traza desde la web, también puedes compartir la URL de la página directamente con otros, lo que les permite ver la misma traza.

### Enabling stack trace samples

Para habilitar el muestreo de la pila de llamadas en Tracy, construye Julia con estas opciones en tu archivo `Make.user`:

```
WITH_TRACY := 1
WITH_TRACY_CALLSTACKS := 1
USE_BINARYBUILDER_LIBTRACYCLIENT := 0
```

También es posible que necesites ejecutar `make -C deps clean-libtracyclient` para forzar una reconstrucción de Tracy.

Esta función tiene un impacto significativo en el tamaño de la traza y la sobrecarga de perfilado, por lo que se recomienda dejar la muestreo de la pila de llamadas desactivado cuando sea posible, especialmente si tienes la intención de compartir tus archivos de traza en línea.

Tenga en cuenta que el tiempo de ejecución JIT de Julia aún no tiene integración para la simbolificación de Tracy, por lo que las funciones de Julia generalmente serán desconocidas en estas trazas de pila.

## Intel VTune (ITTAPI) Profiler

*Esta sección aún está por escribirse.*
