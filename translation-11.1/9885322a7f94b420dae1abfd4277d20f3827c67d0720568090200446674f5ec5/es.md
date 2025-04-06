```
unlock(lock)
```

Libera la propiedad del `lock`.

Si este es un bloqueo recursivo que se ha adquirido antes, decrementa un contador interno y retorna inmediatamente.
