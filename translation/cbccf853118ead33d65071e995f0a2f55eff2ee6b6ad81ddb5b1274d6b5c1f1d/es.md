```
pipeline(from, to, ...)
```

Crea un pipeline desde una fuente de datos hasta un destino. La fuente y el destino pueden ser comandos, flujos de E/S, cadenas o resultados de otras llamadas a `pipeline`. Al menos un argumento debe ser un comando. Las cadenas se refieren a nombres de archivos. Cuando se llama con más de dos argumentos, se encadenan de izquierda a derecha. Por ejemplo, `pipeline(a,b,c)` es equivalente a `pipeline(pipeline(a,b),c)`. Esto proporciona una forma más concisa de especificar pipelines de múltiples etapas.

**Ejemplos**:

```julia
run(pipeline(`ls`, `grep xyz`))
run(pipeline(`ls`, "out.txt"))
run(pipeline("out.txt", `grep xyz`))
```
