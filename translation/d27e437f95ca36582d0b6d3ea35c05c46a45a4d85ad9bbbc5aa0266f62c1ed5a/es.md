```
put!(rr::Future, v)
```

Almacena un valor en un [`Future`](@ref) `rr`. Los `Future`s son referencias remotas de escritura única. Un `put!` en un `Future` ya establecido lanza una `Excepción`. Todas las llamadas remotas asíncronas devuelven `Future`s y establecen el valor al valor de retorno de la llamada al completarse.
