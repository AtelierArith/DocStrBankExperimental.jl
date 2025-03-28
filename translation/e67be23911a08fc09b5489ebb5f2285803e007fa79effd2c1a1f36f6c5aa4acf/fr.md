```
run(command, args...; wait::Bool = true)
```

Exécute un objet de commande, construit avec des backticks (voir la section [Exécution de programmes externes](@ref) dans le manuel). Lève une erreur si quelque chose ne va pas, y compris si le processus se termine avec un statut non nul (lorsque `wait` est vrai).

Les `args...` vous permettent de passer des descripteurs de fichiers à la commande, et sont ordonnés comme des descripteurs de fichiers unix réguliers (par exemple `stdin, stdout, stderr, FD(3), FD(4)...`).

Si `wait` est faux, le processus s'exécute de manière asynchrone. Vous pouvez ensuite attendre qu'il se termine et vérifier son statut de sortie en appelant `success` sur l'objet de processus retourné.

Lorsque `wait` est faux, les flux d'E/S du processus sont dirigés vers `devnull`. Lorsque `wait` est vrai, les flux d'E/S sont partagés avec le processus parent. Utilisez [`pipeline`](@ref) pour contrôler la redirection des E/S.
