```
dlsym_e(handle, sym)
```

Busca un símbolo de un manejador de biblioteca compartida, devuelve silenciosamente `C_NULL` en caso de fallo en la búsqueda. Este método ahora está en desuso a favor de `dlsym(handle, sym; throw_error=false)`.
