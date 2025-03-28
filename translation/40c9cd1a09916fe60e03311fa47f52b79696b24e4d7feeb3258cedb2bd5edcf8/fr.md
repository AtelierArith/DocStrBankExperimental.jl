```
remotecall_wait(f, id::Integer, args...; kwargs...)
```

Effectuez un `wait(remotecall(...))` plus rapide en un seul message sur le `Worker` spécifié par l'identifiant du worker `id`. Les arguments de mot-clé, le cas échéant, sont transmis à `f`.

Voir aussi [`wait`](@ref) et [`remotecall`](@ref).
