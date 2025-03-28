```
InterruptException()
```

Le processus a été arrêté par une interruption du terminal (CTRL+C).

Notez que, dans un script Julia démarré sans l'option `-i` (interactive), `InterruptException` n'est pas lancé par défaut. Appeler [`Base.exit_on_sigint(false)`](@ref Base.exit_on_sigint) dans le script peut rétablir le comportement du REPL. Alternativement, un script Julia peut être démarré avec

```sh
julia -e "include(popfirst!(ARGS))" script.jl
```

pour permettre à `InterruptException` d'être lancé par CTRL+C pendant l'exécution.
