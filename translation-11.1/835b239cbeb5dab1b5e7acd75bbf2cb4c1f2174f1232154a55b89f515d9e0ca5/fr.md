```
exit_on_sigint(on::Bool)
```

Définir le drapeau `exit_on_sigint` de l'environnement d'exécution Julia. Si `false`, Ctrl-C (SIGINT) est capturable comme [`InterruptException`](@ref) dans un bloc `try`. C'est le comportement par défaut dans REPL, tout code exécuté via `-e` et `-E` et dans un script Julia exécuté avec l'option `-i`.

Si `true`, `InterruptException` n'est pas lancé par Ctrl-C. L'exécution de code lors d'un tel événement nécessite [`atexit`](@ref). C'est le comportement par défaut dans un script Julia exécuté sans l'option `-i`.

!!! compat "Julia 1.5"
    La fonction `exit_on_sigint` nécessite au moins Julia 1.5.

