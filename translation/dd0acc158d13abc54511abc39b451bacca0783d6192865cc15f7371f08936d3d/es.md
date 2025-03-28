```
pmap(f, [::AbstractWorkerPool], c...; distributed=true, batch_size=1, on_error=nothing, retry_delays=[], retry_check=nothing) -> colección
```

Transforma la colección `c` aplicando `f` a cada elemento utilizando los trabajadores y tareas disponibles.

Para múltiples argumentos de colección, aplica `f` elemento por elemento.

Ten en cuenta que `f` debe estar disponible para todos los procesos de trabajo; consulta [Disponibilidad de Código y Carga de Paquetes](@ref code-availability) para más detalles.

Si no se especifica un grupo de trabajadores, se utilizarán todos los trabajadores disponibles a través de un [`CachingPool`](@ref).

Por defecto, `pmap` distribuye la computación entre todos los trabajadores especificados. Para usar solo el proceso local y distribuir entre tareas, especifica `distributed=false`. Esto es equivalente a usar [`asyncmap`](@ref). Por ejemplo, `pmap(f, c; distributed=false)` es equivalente a `asyncmap(f,c; ntasks=()->nworkers())`

`pmap` también puede usar una mezcla de procesos y tareas a través del argumento `batch_size`. Para tamaños de lote mayores que 1, la colección se procesa en múltiples lotes, cada uno de longitud `batch_size` o menos. Un lote se envía como una sola solicitud a un trabajador libre, donde un [`asyncmap`](@ref) local procesa elementos del lote utilizando múltiples tareas concurrentes.

Cualquier error detiene a `pmap` de procesar el resto de la colección. Para anular este comportamiento, puedes especificar una función de manejo de errores a través del argumento `on_error` que toma un solo argumento, es decir, la excepción. La función puede detener el procesamiento volviendo a lanzar el error, o, para continuar, devolver cualquier valor que luego se devuelve en línea con los resultados al llamador.

Considera los siguientes dos ejemplos. El primero devuelve el objeto de excepción en línea, el segundo un 0 en lugar de cualquier excepción:

```julia-repl
julia> pmap(x->iseven(x) ? error("foo") : x, 1:4; on_error=identity)
4-element Array{Any,1}:
 1
  ErrorException("foo")
 3
  ErrorException("foo")

julia> pmap(x->iseven(x) ? error("foo") : x, 1:4; on_error=ex->0)
4-element Array{Int64,1}:
 1
 0
 3
 0
```

Los errores también se pueden manejar reintentando cálculos fallidos. Los argumentos clave `retry_delays` y `retry_check` se pasan a [`retry`](@ref) como argumentos clave `delays` y `check` respectivamente. Si se especifica el agrupamiento, y un lote entero falla, todos los elementos en el lote se reintentan.

Ten en cuenta que si se especifican tanto `on_error` como `retry_delays`, el gancho `on_error` se llama antes de reintentar. Si `on_error` no lanza (o vuelve a lanzar) una excepción, el elemento no se reintentará.

Ejemplo: En caso de errores, reintenta `f` en un elemento un máximo de 3 veces sin ningún retraso entre reintentos.

```julia
pmap(f, c; retry_delays = zeros(3))
```

Ejemplo: Reintenta `f` solo si la excepción no es del tipo [`InexactError`](@ref), con retrasos que aumentan exponencialmente hasta 3 veces. Devuelve un `NaN` en lugar de todas las ocurrencias de `InexactError`.

```julia
pmap(f, c; on_error = e->(isa(e, InexactError) ? NaN : rethrow()), retry_delays = ExponentialBackOff(n = 3))
```
