```
redirect_stdout(f::Function, stream)
```

Exécutez la fonction `f` tout en redirigeant [`stdout`](@ref) vers `stream`. Une fois terminé, [`stdout`](@ref) est restauré à son paramètre précédent.
