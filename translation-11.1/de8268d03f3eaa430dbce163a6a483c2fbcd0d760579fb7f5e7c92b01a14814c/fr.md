```
realloc(addr::Ptr, size::Integer) -> Ptr{Cvoid}
```

Appelez `realloc` de la bibliothèque standard C.

Voir l'avertissement dans la documentation pour [`free`](@ref) concernant l'utilisation uniquement de cette fonction sur la mémoire obtenue à l'origine à partir de [`malloc`](@ref).
