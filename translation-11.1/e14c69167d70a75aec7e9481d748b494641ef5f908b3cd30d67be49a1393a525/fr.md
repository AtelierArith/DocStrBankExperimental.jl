```
dlopen_e(libfile::AbstractString [, flags::Integer])
```

Semblable à [`dlopen`](@ref), sauf qu'il retourne `C_NULL` au lieu de lever des erreurs. Cette méthode est maintenant obsolète au profit de `dlopen(libfile::AbstractString [, flags::Integer]; throw_error=false)`.
