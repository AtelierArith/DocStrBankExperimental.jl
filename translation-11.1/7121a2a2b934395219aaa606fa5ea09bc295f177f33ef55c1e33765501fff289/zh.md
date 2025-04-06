```
Sys.CPU_THREADS::Int
```

系统中可用的逻辑 CPU 核心数量，即 CPU 可以同时运行的线程数量。请注意，这不一定是 CPU 核心的数量，例如，在存在 [超线程](https://en.wikipedia.org/wiki/Hyper-threading) 的情况下。

有关更多信息，包括物理核心的数量，请参见 Hwloc.jl 或 CpuId.jl。
