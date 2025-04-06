```
@arg_test arg1 arg2 ... corps
```

Le macro `@arg_test` est utilisé pour convertir les fonctions `arg` fournies par `arg_readers` et `arg_writers` en valeurs d'argument réelles. Lorsque vous écrivez `@arg_test arg corps`, cela équivaut à `arg(arg -> corps)`.
