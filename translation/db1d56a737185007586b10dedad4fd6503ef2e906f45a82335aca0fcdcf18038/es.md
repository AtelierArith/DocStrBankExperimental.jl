```
dot(x, y)
x ⋅ y
```

Calcula el producto punto entre dos vectores. Para vectores complejos, el primer vector se conjuga.

`dot` también funciona en objetos iterables arbitrarios, incluyendo arreglos de cualquier dimensión, siempre que `dot` esté definido en los elementos.

`dot` es semánticamente equivalente a `sum(dot(vx,vy) for (vx,vy) in zip(x, y))`, con la restricción adicional de que los argumentos deben tener longitudes iguales.

`x ⋅ y` (donde `⋅` se puede escribir completando con tabulador `\cdot` en el REPL) es un sinónimo de `dot(x, y)`.

# Ejemplos

```jldoctest
julia> dot([1; 1], [2; 3])
5

julia> dot([im; im], [1; 1])
0 - 2im

julia> dot(1:5, 2:6)
70

julia> x = fill(2., (5,5));

julia> y = fill(3., (5,5));

julia> dot(x, y)
150.0
```
