```
@threadcall((cfunc, clib), rettype, (argtypes...), argvals...)
```

Das `@threadcall`-Makro wird auf die gleiche Weise wie [`ccall`](@ref) aufgerufen, führt die Arbeit jedoch in einem anderen Thread aus. Dies ist nützlich, wenn Sie eine blockierende C-Funktion aufrufen möchten, ohne den aktuellen `julia`-Thread zu blockieren. Die Parallelität ist durch die Größe des libuv-Thread-Pools begrenzt, der standardmäßig 4 Threads umfasst, aber durch Setzen der Umgebungsvariable `UV_THREADPOOL_SIZE` erhöht werden kann, und der `julia`-Prozess muss neu gestartet werden.

Beachten Sie, dass die aufgerufene Funktion niemals in Julia zurückrufen sollte.
