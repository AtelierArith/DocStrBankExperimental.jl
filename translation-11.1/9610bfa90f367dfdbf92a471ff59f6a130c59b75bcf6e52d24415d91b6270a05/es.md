```
atreplinit(f)
```

Registra una función de un argumento que se llamará antes de que se inicialice la interfaz REPL en sesiones interactivas; esto es útil para personalizar la interfaz. El argumento de `f` es el objeto REPL. Esta función debe ser llamada desde dentro del archivo de inicialización `.julia/config/startup.jl`.
