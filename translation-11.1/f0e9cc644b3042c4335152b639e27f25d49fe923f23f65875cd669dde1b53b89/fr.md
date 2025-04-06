```
timedwait(testcb, timeout::Real; pollint::Real=0.1)
```

Attendez jusqu'à ce que `testcb()` retourne `true` ou que `timeout` secondes se soient écoulées, selon ce qui se produit en premier. La fonction de test est interrogée toutes les `pollint` secondes. La valeur minimale pour `pollint` est de 0,001 secondes, c'est-à-dire 1 milliseconde.

Retourne `:ok` ou `:timed_out`.

# Exemples

```jldoctest
julia> cb() = (sleep(5); return);

julia> t = @async cb();

julia> timedwait(()->istaskdone(t), 1)
:timed_out

julia> timedwait(()->istaskdone(t), 6.5)
:ok
```
