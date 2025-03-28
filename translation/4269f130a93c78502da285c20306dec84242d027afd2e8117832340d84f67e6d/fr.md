```
redirect_stdin(f::Function, stream)
```

Exécutez la fonction `f` tout en redirigeant [`stdin`](@ref) vers `stream`. Une fois terminé, [`stdin`](@ref) est restauré à son paramètre précédent.
