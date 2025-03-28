```
RemoteChannel(pid::Integer=myid())
```

Crea una referencia a un `Channel{Any}(1)` en el proceso `pid`. El `pid` por defecto es el proceso actual.

```
RemoteChannel(f::Function, pid::Integer=myid())
```

Crea referencias a canales remotos de un tamaño y tipo específicos. `f` es una función que, cuando se ejecuta en `pid`, debe devolver una implementación de un `AbstractChannel`.

Por ejemplo, `RemoteChannel(()->Channel{Int}(10), pid)`, devolverá una referencia a un canal de tipo `Int` y tamaño 10 en `pid`.

El `pid` por defecto es el proceso actual.
