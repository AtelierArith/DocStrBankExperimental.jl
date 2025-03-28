```
CachingPool(workers::Vector{Int})
```

Una implementación de un `AbstractWorkerPool`. [`remote`](@ref), [`remotecall_fetch`](@ref), [`pmap`](@ref) (y otras llamadas remotas que ejecutan funciones de forma remota) se benefician de almacenar en caché las funciones serializadas/deserializadas en los nodos de trabajo, especialmente los cierres (que pueden capturar grandes cantidades de datos).

La caché remota se mantiene durante la vida útil del objeto `CachingPool` devuelto. Para limpiar la caché antes, usa `clear!(pool)`.

Para las variables globales, solo se capturan los enlaces en un cierre, no los datos. Se pueden usar bloques `let` para capturar datos globales.

# Ejemplos

```julia
const foo = rand(10^8);
wp = CachingPool(workers())
let foo = foo
    pmap(i -> sum(foo) + i, wp, 1:100);
end
```

Lo anterior transferiría `foo` solo una vez a cada trabajador.
