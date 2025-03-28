```
put!(rr::Future, v)
```

Stockez une valeur dans un [`Future`](@ref) `rr`. Les `Future`s sont des références distantes en écriture unique. Un `put!` sur un `Future` déjà défini déclenche une `Exception`. Tous les appels distants asynchrones renvoient des `Future`s et définissent la valeur sur la valeur de retour de l'appel une fois terminé.
