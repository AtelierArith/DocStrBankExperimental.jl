```
redirect_stderr(f::Function, stream)
```

Exécutez la fonction `f` tout en redirigeant [`stderr`](@ref) vers `stream`. Une fois terminé, [`stderr`](@ref) est restauré à son paramètre précédent.
