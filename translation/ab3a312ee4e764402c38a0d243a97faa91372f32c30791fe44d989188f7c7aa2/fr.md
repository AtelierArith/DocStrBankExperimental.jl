```
@threadcall((cfunc, clib), rettype, (argtypes...), argvals...)
```

Le macro `@threadcall` est appelé de la même manière que [`ccall`](@ref) mais effectue le travail dans un thread différent. Cela est utile lorsque vous souhaitez appeler une fonction C bloquante sans provoquer le blocage du thread `julia` actuel. La concurrence est limitée par la taille du pool de threads libuv, qui par défaut est de 4 threads mais peut être augmentée en définissant la variable d'environnement `UV_THREADPOOL_SIZE` et en redémarrant le processus `julia`.

Notez que la fonction appelée ne doit jamais rappeler Julia.
