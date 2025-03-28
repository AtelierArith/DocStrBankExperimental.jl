```
fetch(x::Future)
```

Espera y obtiene el valor de un [`Future`](@ref). El valor obtenido se almacena en caché localmente. Las llamadas posteriores a `fetch` en la misma referencia devuelven el valor en caché. Si el valor remoto es una excepción, lanza una [`RemoteException`](@ref) que captura la excepción remota y la traza de la pila.
