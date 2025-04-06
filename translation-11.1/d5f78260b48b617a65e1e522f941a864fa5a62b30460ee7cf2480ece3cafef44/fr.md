```
start_worker([out::IO=stdout], cookie::AbstractString=readline(stdin); close_stdin::Bool=true, stderr_to_stdout::Bool=true)
```

`start_worker` est une fonction interne qui est le point d'entrée par défaut pour les processus de travail se connectant via TCP/IP. Elle configure le processus en tant que travailleur du cluster Julia.

Les informations host:port sont écrites dans le flux `out` (par défaut stdout).

La fonction lit le cookie depuis stdin si nécessaire, et écoute sur un port libre (ou si spécifié, le port dans l'option de ligne de commande `--bind-to`) et planifie des tâches pour traiter les connexions TCP entrantes et les demandes. Elle ferme également (optionnellement) stdin et redirige stderr vers stdout.

Elle ne retourne pas.
