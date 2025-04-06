```
reenable_sigint(f::Function)
```

Réactive le gestionnaire Ctrl-C pendant l'exécution d'une fonction. Inverse temporairement l'effet de [`disable_sigint`](@ref).
