```
Timer(callback::Function, delay; interval = 0)
```

Créez un minuteur qui exécute la fonction `callback` à chaque expiration du minuteur.

Les tâches en attente sont réveillées et la fonction `callback` est appelée après un délai initial de `delay` secondes, puis se répète avec l'intervalle donné en secondes. Si `interval` est égal à `0`, le callback n'est exécuté qu'une seule fois. La fonction `callback` est appelée avec un seul argument, le minuteur lui-même. Arrêtez un minuteur en appelant `close`. Le `callback` peut encore être exécuté une dernière fois, si le minuteur a déjà expiré.

# Exemples

Ici, le premier nombre est imprimé après un délai de deux secondes, puis les nombres suivants sont imprimés rapidement.

```julia-repl
julia> begin
           i = 0
           cb(timer) = (global i += 1; println(i))
           t = Timer(cb, 2, interval=0.2)
           wait(t)
           sleep(0.5)
           close(t)
       end
1
2
3
```
