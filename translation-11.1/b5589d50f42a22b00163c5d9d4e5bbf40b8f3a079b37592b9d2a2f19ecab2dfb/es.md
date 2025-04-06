```
dlsym(handle, sym; throw_error::Bool = true)
```

Busca un símbolo de un manejador de biblioteca compartida, devuelve un puntero a función callable en caso de éxito.

Si no se puede encontrar el símbolo, este método lanza un error, a menos que el argumento clave `throw_error` esté configurado en `false`, en cuyo caso este método devuelve `nothing`.
