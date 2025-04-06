```
arg_isdir(f::Function, arg::AbstractString) -> f(arg)
```

La fonction `arg_isdir` prend `arg` qui doit être le chemin vers un répertoire existant (une erreur est levée sinon) et passe ce chemin à `f`, retournant finalement le résultat de `f(arg)`. C'est définitivement l'outil le moins utile proposé par `ArgTools` et existe principalement pour la symétrie avec `arg_mkdir` et pour fournir des messages d'erreur cohérents.
