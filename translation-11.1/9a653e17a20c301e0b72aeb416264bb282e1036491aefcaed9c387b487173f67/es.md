```
@static
```

Evalúa parcialmente una expresión en el tiempo de análisis.

Por ejemplo, `@static Sys.iswindows() ? foo : bar` evaluará `Sys.iswindows()` e insertará ya sea `foo` o `bar` en la expresión. Esto es útil en casos donde un constructo sería inválido en otras plataformas, como un `ccall` a una función inexistente. `@static if Sys.isapple() foo end` y `@static foo <&&,||> bar` también son sintaxis válidas.
