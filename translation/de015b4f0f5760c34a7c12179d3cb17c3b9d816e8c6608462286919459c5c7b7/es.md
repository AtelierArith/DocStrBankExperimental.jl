```
kill(p::Process, signum=Base.SIGTERM)
```

Envía una señal a un proceso. El valor predeterminado es terminar el proceso. Devuelve con éxito si el proceso ya ha salido, pero lanza un error si la terminación del proceso falló por otras razones (por ejemplo, permisos insuficientes).
