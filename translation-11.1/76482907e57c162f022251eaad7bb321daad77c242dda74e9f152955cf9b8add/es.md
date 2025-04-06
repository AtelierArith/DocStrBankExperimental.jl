```
sort!(v; alg::Algorithm=defalg(v), lt=isless, by=identity, rev::Bool=false, order::Ordering=Forward)
```

Ordena el vector `v` en su lugar. Se utiliza un algoritmo estable por defecto: se preserva el orden de los elementos que se comparan como iguales. Se puede seleccionar un algoritmo específico a través de la palabra clave `alg` (ver [Algoritmos de Ordenación](@ref) para los algoritmos disponibles).

Los elementos se transforman primero con la función `by` y luego se comparan de acuerdo con la función `lt` o el orden `order`. Finalmente, el orden resultante se invierte si `rev=true` (esto preserva la estabilidad hacia adelante: los elementos que se comparan como iguales no se invierten). La implementación actual aplica la transformación `by` antes de cada comparación en lugar de una vez por elemento.

No se permite pasar un `lt` diferente de `isless` junto con un `order` diferente de [`Base.Order.Forward`](@ref) o [`Base.Order.Reverse`](@ref); de lo contrario, todas las opciones son independientes y se pueden usar juntas en todas las combinaciones posibles. Tenga en cuenta que `order` también puede incluir una transformación "by", en cuyo caso se aplica después de la definida con la palabra clave `by`. Para más información sobre los valores de `order`, consulte la documentación sobre [Ordenamientos Alternativos](@ref).

Las relaciones entre dos elementos se definen de la siguiente manera (con "menor" y "mayor" intercambiados cuando `rev=true`):

  * `x` es menor que `y` si `lt(by(x), by(y))` (o `Base.Order.lt(order, by(x), by(y))`) devuelve verdadero.
  * `x` es mayor que `y` si `y` es menor que `x`.
  * `x` e `y` son equivalentes si ninguno es menor que el otro ("incomparable" a veces se usa como sinónimo de "equivalente").

El resultado de `sort!` está ordenado en el sentido de que cada elemento es mayor o equivalente al anterior.

La función `lt` debe definir un orden débil estricto, es decir, debe ser

  * irreflexiva: `lt(x, x)` siempre devuelve `false`,
  * asimétrica: si `lt(x, y)` devuelve `true`, entonces `lt(y, x)` devuelve `false`,
  * transitiva: `lt(x, y) && lt(y, z)` implica `lt(x, z)`,
  * transitiva en equivalencia: `!lt(x, y) && !lt(y, x)` y `!lt(y, z) && !lt(z, y)` juntas implican `!lt(x, z) && !lt(z, x)`. En palabras: si `x` e `y` son equivalentes y `y` y `z` son equivalentes, entonces `x` y `z` deben ser equivalentes.

Por ejemplo, `<` es una función `lt` válida para valores `Int`, pero `≤` no lo es: viola la irreflexividad. Para valores `Float64`, incluso `<` es inválido ya que viola la cuarta condición: `1.0` y `NaN` son equivalentes y también lo son `NaN` y `2.0`, pero `1.0` y `2.0` no son equivalentes.

Véase también [`sort`](@ref), [`sortperm`](@ref), [`sortslices`](@ref), [`partialsort!`](@ref), [`partialsortperm`](@ref), [`issorted`](@ref), [`searchsorted`](@ref), [`insorted`](@ref), [`Base.Order.ord`](@ref).

# Ejemplos

```jldoctest
julia> v = [3, 1, 2]; sort!(v); v
3-element Vector{Int64}:
 1
 2
 3

julia> v = [3, 1, 2]; sort!(v, rev = true); v
3-element Vector{Int64}:
 3
 2
 1

julia> v = [(1, "c"), (3, "a"), (2, "b")]; sort!(v, by = x -> x[1]); v
3-element Vector{Tuple{Int64, String}}:
 (1, "c")
 (2, "b")
 (3, "a")

julia> v = [(1, "c"), (3, "a"), (2, "b")]; sort!(v, by = x -> x[2]); v
3-element Vector{Tuple{Int64, String}}:
 (3, "a")
 (2, "b")
 (1, "c")

julia> sort(0:3, by=x->x-2, order=Base.Order.By(abs)) # same as sort(0:3, by=abs(x->x-2))
4-element Vector{Int64}:
 2
 1
 3
 0

julia> sort([2, NaN, 1, NaN, 3]) # correct sort with default lt=isless
5-element Vector{Float64}:
   1.0
   2.0
   3.0
 NaN
 NaN

julia> sort([2, NaN, 1, NaN, 3], lt=<) # wrong sort due to invalid lt. This behavior is undefined.
5-element Vector{Float64}:
   2.0
 NaN
   1.0
 NaN
   3.0
```
