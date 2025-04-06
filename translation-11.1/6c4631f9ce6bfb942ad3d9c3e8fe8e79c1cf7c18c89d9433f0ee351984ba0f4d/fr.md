```
pipeline(command; stdin, stdout, stderr, append=false)
```

Redirige l'entrée/sortie vers ou depuis la commande donnée `command`. Les arguments clés spécifient quels flux de la commande doivent être redirigés. `append` contrôle si la sortie de fichier s'ajoute au fichier. C'est une version plus générale de la fonction `pipeline` à 2 arguments. `pipeline(from, to)` est équivalent à `pipeline(from, stdout=to)` lorsque `from` est une commande, et à `pipeline(to, stdin=from)` lorsque `from` est un autre type de source de données.

**Exemples**:

```julia
run(pipeline(`dothings`, stdout="out.txt", stderr="errs.txt"))
run(pipeline(`update`, stdout="log.txt", append=true))
```
