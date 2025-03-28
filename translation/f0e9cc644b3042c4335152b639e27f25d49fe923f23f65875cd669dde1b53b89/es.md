```
timedwait(testcb, timeout::Real; pollint::Real=0.1)
```

Espera hasta que `testcb()` devuelva `true` o hayan pasado `timeout` segundos, lo que ocurra primero. La función de prueba se consulta cada `pollint` segundos. El valor mínimo para `pollint` es 0.001 segundos, es decir, 1 milisegundo.

Devuelve `:ok` o `:timed_out`.

# Ejemplos

```jldoctest
julia> cb() = (sleep(5); return);

julia> t = @async cb();

julia> timedwait(()->istaskdone(t), 1)
:timed_out

julia> timedwait(()->istaskdone(t), 6.5)
:ok
```
