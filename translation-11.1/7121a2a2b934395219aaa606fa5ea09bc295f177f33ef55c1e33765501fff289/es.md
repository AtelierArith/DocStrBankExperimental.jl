```
Sys.CPU_THREADS::Int
```

El número de núcleos lógicos de CPU disponibles en el sistema, es decir, el número de hilos que la CPU puede ejecutar de manera concurrente. Tenga en cuenta que este no es necesariamente el número de núcleos de CPU, por ejemplo, en presencia de [hyper-threading](https://en.wikipedia.org/wiki/Hyper-threading).

Consulte Hwloc.jl o CpuId.jl para obtener información ampliada, incluido el número de núcleos físicos.
