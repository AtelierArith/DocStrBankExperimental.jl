```
pipeline(from, to, ...)
```

Créez un pipeline d'une source de données à une destination. La source et la destination peuvent être des commandes, des flux d'E/S, des chaînes de caractères ou des résultats d'autres appels à `pipeline`. Au moins un argument doit être une commande. Les chaînes de caractères font référence à des noms de fichiers. Lorsqu'il est appelé avec plus de deux arguments, ils sont enchaînés de gauche à droite. Par exemple, `pipeline(a,b,c)` est équivalent à `pipeline(pipeline(a,b),c)`. Cela fournit un moyen plus concis de spécifier des pipelines à plusieurs étapes.

**Exemples**:

```julia
run(pipeline(`ls`, `grep xyz`))
run(pipeline(`ls`, "out.txt"))
run(pipeline("out.txt", `grep xyz`))
```
