```
IndexLinear()
```

Subtipo de [`IndexStyle`](@ref) utilizado para describir arreglos que son indexados de manera óptima por un índice lineal.

Un estilo de indexación lineal utiliza un índice entero para describir la posición en el arreglo (incluso si es un arreglo multidimensional) y se utiliza un ordenamiento por columnas para acceder eficientemente a los elementos. Esto significa que solicitar [`eachindex`](@ref) de un arreglo que es `IndexLinear` devolverá un rango unidimensional simple, incluso si es multidimensional.

Un arreglo personalizado que reporta su `IndexStyle` como `IndexLinear` solo necesita implementar la indexación (y la asignación indexada) con un único índice `Int`; todas las demás expresiones de indexación —incluyendo accesos multidimensionales— se recalcularán al índice lineal. Por ejemplo, si `A` fuera una matriz personalizada de `2×3` con indexación lineal, y referenciáramos `A[1, 3]`, esto se recalcularía al índice lineal equivalente y llamaría a `A[5]` ya que `1 + 2*(3 - 1) = 5`.

Ver también [`IndexCartesian`](@ref).
