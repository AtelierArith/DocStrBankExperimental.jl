```
@time_imports
```

Una macro para ejecutar una expresión y producir un informe de cualquier tiempo gastado importando paquetes y sus dependencias. Cualquier tiempo de compilación se informará como un porcentaje, y cuánto de eso fue recompilación, si la hubo.

Se imprime una línea por paquete o extensión de paquete. La duración mostrada es el tiempo para importar ese paquete en sí, sin incluir el tiempo para cargar ninguna de sus dependencias.

En Julia 1.9+ [extensiones de paquete](@ref man-extensions) se mostrarán como Padre → Extensión.

!!! nota
    Durante el proceso de carga, un paquete importa secuencialmente todas sus dependencias, no solo sus dependencias directas.


```julia-repl
julia> @time_imports using CSV
     50.7 ms  Parsers 17.52% tiempo de compilación
      0.2 ms  DataValueInterfaces
      1.6 ms  DataAPI
      0.1 ms  IteratorInterfaceExtensions
      0.1 ms  TableTraits
     17.5 ms  Tables
     26.8 ms  PooledArrays
    193.7 ms  SentinelArrays 75.12% tiempo de compilación
      8.6 ms  InlineStrings
     20.3 ms  WeakRefStrings
      2.0 ms  TranscodingStreams
      1.4 ms  Zlib_jll
      1.8 ms  CodecZlib
      0.8 ms  Compat
     13.1 ms  FilePathsBase 28.39% tiempo de compilación
   1681.2 ms  CSV 92.40% tiempo de compilación
```

!!! compat "Julia 1.8"
    Esta macro requiere al menos Julia 1.8

