```
remotecall_fetch(f, id::Integer, args...; kwargs...)
```

Effectue `fetch(remotecall(...))` en un seul message. Les arguments de mot-clé, le cas échéant, sont transmis à `f`. Toute exception distante est capturée dans une [`RemoteException`](@ref) et levée.

Voir aussi [`fetch`](@ref) et [`remotecall`](@ref).

# Exemples

```julia-repl
$ julia -p 2

julia> remotecall_fetch(sqrt, 2, 4)
2.0

julia> remotecall_fetch(sqrt, 2, -4)
ERROR: Sur le worker 2 :
DomainError avec -4.0 :
sqrt a été appelé avec un argument réel négatif mais ne renverra qu'un résultat complexe s'il est appelé avec un argument complexe. Essayez sqrt(Complex(x)).
...
```
