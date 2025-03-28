```
Sys.CPU_THREADS::Int
```

Le nombre de cœurs logiques de CPU disponibles dans le système, c'est-à-dire le nombre de threads que le CPU peut exécuter simultanément. Notez que ce n'est pas nécessairement le nombre de cœurs de CPU, par exemple, en présence de [hyper-threading](https://en.wikipedia.org/wiki/Hyper-threading).

Voir Hwloc.jl ou CpuId.jl pour des informations étendues, y compris le nombre de cœurs physiques.
