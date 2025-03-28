```
IndexCartesian()
```

Subtipo de [`IndexStyle`](@ref) utilizado para describir arreglos que son indexados de manera óptima por un índice cartesiano. Este es el valor predeterminado para nuevos subtipos de [`AbstractArray`](@ref) personalizados.

Un estilo de indexación cartesiana utiliza múltiples índices enteros para describir la posición en un arreglo multidimensional, con exactamente un índice por dimensión. Esto significa que solicitar [`eachindex`](@ref) de un arreglo que es `IndexCartesian` devolverá un rango de [`CartesianIndices`](@ref).

Un arreglo personalizado de `N` dimensiones que reporta su `IndexStyle` como `IndexCartesian` necesita implementar la indexación (y la asignación indexada) con exactamente `N` índices `Int`; todas las demás expresiones de indexación —incluida la indexación lineal— se recalcularán a la ubicación cartesiana equivalente. Por ejemplo, si `A` fuera una matriz personalizada de `2×3` con indexación cartesiana, y referenciáramos `A[5]`, esto se recalcularía al índice cartesiano equivalente y llamaría a `A[1, 3]` ya que `5 = 1 + 2*(3 - 1)`.

Es significativamente más costoso calcular índices cartesianos a partir de un índice lineal que hacerlo en la otra dirección. La primera operación requiere división —una operación muy costosa— mientras que la última solo utiliza multiplicación y adición y es esencialmente gratuita. Esta asimetría significa que es mucho más costoso usar indexación lineal con un arreglo `IndexCartesian` que usar indexación cartesiana con un arreglo `IndexLinear`.

Ver también [`IndexLinear`](@ref).
