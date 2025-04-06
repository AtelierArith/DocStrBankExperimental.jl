```
@fastmath expr
```

Ejecuta una versión transformada de la expresión, que llama a funciones que pueden violar las semánticas estrictas de IEEE. Esto permite la operación más rápida posible, pero los resultados son indefinidos; ten cuidado al hacer esto, ya que puede cambiar los resultados numéricos.

Esto establece las [banderas de Fast-Math de LLVM](https://llvm.org/docs/LangRef.html#fast-math-flags), y corresponde a la opción `-ffast-math` en clang. Consulta [las notas sobre anotaciones de rendimiento](@ref man-performance-annotations) para más detalles.

# Ejemplos

```jldoctest
julia> @fastmath 1+2
3

julia> @fastmath(sin(3))
0.1411200080598672
```
