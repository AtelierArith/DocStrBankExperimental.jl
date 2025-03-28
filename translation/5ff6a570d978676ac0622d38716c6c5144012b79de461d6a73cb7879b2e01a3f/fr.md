```
RemoteChannel(pid::Integer=myid())
```

Faites référence à un `Channel{Any}(1)` sur le processus `pid`. Le `pid` par défaut est le processus actuel.

```
RemoteChannel(f::Function, pid::Integer=myid())
```

Créez des références à des canaux distants d'une taille et d'un type spécifiques. `f` est une fonction qui, lorsqu'elle est exécutée sur `pid`, doit renvoyer une implémentation d'un `AbstractChannel`.

Par exemple, `RemoteChannel(()->Channel{Int}(10), pid)`, renverra une référence à un canal de type `Int` et de taille 10 sur `pid`.

Le `pid` par défaut est le processus actuel.
