```
iterate(iter [, state]) -> Union{Nothing, Tuple{Any, Any}}
```

Avanza el iterador para obtener el siguiente elemento. Si no quedan elementos, se debe devolver `nothing`. De lo contrario, se debe devolver una tupla de 2 elementos que contiene el siguiente elemento y el nuevo estado de iteración.
