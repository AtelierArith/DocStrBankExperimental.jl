```
@threadcall((cfunc, clib), rettype, (argtypes...), argvals...)
```

El macro `@threadcall` se llama de la misma manera que [`ccall`](@ref) pero realiza el trabajo en un hilo diferente. Esto es útil cuando deseas llamar a una función C bloqueante sin causar que el hilo actual de `julia` se bloquee. La concurrencia está limitada por el tamaño del grupo de hilos de libuv, que por defecto es de 4 hilos, pero se puede aumentar configurando la variable de entorno `UV_THREADPOOL_SIZE` y reiniciando el proceso de `julia`.

Ten en cuenta que la función llamada nunca debe volver a llamar a Julia.
