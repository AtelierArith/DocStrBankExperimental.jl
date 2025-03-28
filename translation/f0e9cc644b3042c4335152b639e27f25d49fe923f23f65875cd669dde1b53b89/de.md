```
timedwait(testcb, timeout::Real; pollint::Real=0.1)
```

Warten, bis `testcb()` `true` zurückgibt oder `timeout` Sekunden vergangen sind, je nachdem, was zuerst eintritt. Die Testfunktion wird alle `pollint` Sekunden abgefragt. Der Mindestwert für `pollint` beträgt 0,001 Sekunden, das sind 1 Millisekunde.

Gibt `:ok` oder `:timed_out` zurück.

# Beispiele

```jldoctest
julia> cb() = (sleep(5); return);

julia> t = @async cb();

julia> timedwait(()->istaskdone(t), 1)
:timed_out

julia> timedwait(()->istaskdone(t), 6.5)
:ok
```
