```
set_num_threads(n::Integer)
set_num_threads(::Nothing)
```

Définissez le nombre de threads que la bibliothèque BLAS doit utiliser égal à `n::Integer`.

Accepte également `nothing`, auquel cas julia essaie de deviner le nombre par défaut de threads. Passer `nothing` est déconseillé et existe principalement pour des raisons historiques.
