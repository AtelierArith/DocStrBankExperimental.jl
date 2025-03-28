```
devnull
```

Utilizado en una redirección de flujo para descartar todos los datos escritos en él. Esencialmente equivalente a `/dev/null` en Unix o `NUL` en Windows. Uso:

```julia
run(pipeline(`cat test.txt`, devnull))
```
