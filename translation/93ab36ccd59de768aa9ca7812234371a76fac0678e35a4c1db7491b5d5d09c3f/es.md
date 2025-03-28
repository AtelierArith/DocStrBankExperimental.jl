```
isapprox(x, y; atol::Real=0, rtol::Real=atol>0 ? 0 : √eps, nans::Bool=false[, norm::Function])
```

Comparación de igualdad inexacta. Dos números se comparan como iguales si su distancia relativa *o* su distancia absoluta está dentro de los límites de tolerancia: `isapprox` devuelve `true` si `norm(x-y) <= max(atol, rtol*max(norm(x), norm(y)))`. La `atol` predeterminada (tolerancia absoluta) es cero y la `rtol` predeterminada (tolerancia relativa) depende de los tipos de `x` e `y`. El argumento clave `nans` determina si los valores NaN se consideran iguales o no (por defecto es falso).

Para valores de punto flotante reales o complejos, si no se especifica un `atol > 0`, la `rtol` predeterminada es la raíz cuadrada de [`eps`](@ref) del tipo de `x` o `y`, el que sea mayor (menos preciso). Esto corresponde a requerir igualdad de aproximadamente la mitad de los dígitos significativos. De lo contrario, por ejemplo, para argumentos enteros o si se proporciona un `atol > 0`, la `rtol` predeterminada es cero.

El argumento clave `norm` predeterminado es `abs` para numéricos `(x,y)` y `LinearAlgebra.norm` para arreglos (donde a veces es útil una elección alternativa de `norm`). Cuando `x` e `y` son arreglos, si `norm(x-y)` no es finito (es decir, `±Inf` o `NaN`), la comparación se reduce a verificar si todos los elementos de `x` e `y` son aproximadamente iguales componente por componente.

El operador binario `≈` es equivalente a `isapprox` con los argumentos predeterminados, y `x ≉ y` es equivalente a `!isapprox(x,y)`.

Ten en cuenta que `x ≈ 0` (es decir, comparar con cero con las tolerancias predeterminadas) es equivalente a `x == 0` ya que la `atol` predeterminada es `0`. En tales casos, debes proporcionar un `atol` apropiado (o usar `norm(x) ≤ atol`) o reorganizar tu código (por ejemplo, usar `x ≈ y` en lugar de `x - y ≈ 0`). No es posible elegir un `atol` distinto de cero automáticamente porque depende de la escala general (las "unidades") de tu problema: por ejemplo, en `x - y ≈ 0`, `atol=1e-9` es una tolerancia absurdamente pequeña si `x` es el [radio de la Tierra](https://es.wikipedia.org/wiki/Raio_de_la_Tierra) en metros, pero una tolerancia absurdamente grande si `x` es el [radio de un átomo de hidrógeno](https://es.wikipedia.org/wiki/Radio_de_Bohr) en metros.

!!! compat "Julia 1.6"
    Pasar el argumento clave `norm` al comparar argumentos numéricos (no de arreglo) requiere Julia 1.6 o posterior.


# Ejemplos

```jldoctest
julia> isapprox(0.1, 0.15; atol=0.05)
true

julia> isapprox(0.1, 0.15; rtol=0.34)
true

julia> isapprox(0.1, 0.15; rtol=0.33)
false

julia> 0.1 + 1e-10 ≈ 0.1
true

julia> 1e-10 ≈ 0
false

julia> isapprox(1e-10, 0, atol=1e-8)
true

julia> isapprox([10.0^9, 1.0], [10.0^9, 2.0]) # usando `norm`
true
```
