```
Sys.CPU_THREADS::Int
```

Die Anzahl der logischen CPU-Kerne, die im System verfügbar sind, d.h. die Anzahl der Threads, die die CPU gleichzeitig ausführen kann. Beachten Sie, dass dies nicht unbedingt die Anzahl der CPU-Kerne ist, zum Beispiel im Falle von [Hyper-Threading](https://en.wikipedia.org/wiki/Hyper-threading).

Siehe Hwloc.jl oder CpuId.jl für erweiterte Informationen, einschließlich der Anzahl der physischen Kerne.
