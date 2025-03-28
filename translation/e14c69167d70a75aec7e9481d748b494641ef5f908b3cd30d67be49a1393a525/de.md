```
dlopen_e(libfile::AbstractString [, flags::Integer])
```

Ähnlich wie [`dlopen`](@ref), gibt jedoch `C_NULL` zurück, anstatt Fehler auszulösen. Diese Methode ist jetzt veraltet zugunsten von `dlopen(libfile::AbstractString [, flags::Integer]; throw_error=false)`.
