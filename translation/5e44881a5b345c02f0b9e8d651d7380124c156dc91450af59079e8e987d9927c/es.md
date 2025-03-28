```
isdispatchtuple(T)
```

Determina si el tipo `T` es un "tipo hoja de tupla", lo que significa que podría aparecer como una firma de tipo en la dispatch y no tiene subtipos (o supertipos) que podrían aparecer en una llamada. Si `T` no es un tipo, entonces devuelve `false`.
