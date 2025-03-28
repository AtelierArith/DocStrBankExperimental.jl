```
atreplinit(f)
```

Enregistre une fonction à un argument qui sera appelée avant que l'interface REPL ne soit initialisée dans les sessions interactives ; cela est utile pour personnaliser l'interface. L'argument de `f` est l'objet REPL. Cette fonction doit être appelée depuis le fichier d'initialisation `.julia/config/startup.jl`.
