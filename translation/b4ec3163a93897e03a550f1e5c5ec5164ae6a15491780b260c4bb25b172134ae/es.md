```
broadcast(f, As...)
```

Difunde la función `f` sobre los arreglos, tuplas, colecciones, [`Ref`](@ref)s y/o escalares `As`.

La difusión aplica la función `f` sobre los elementos de los argumentos contenedores y los escalares mismos en `As`. Las dimensiones singleton y faltantes se expanden para coincidir con las extensiones de los otros argumentos repitiendo virtualmente el valor. Por defecto, solo se consideran un número limitado de tipos como escalares, incluyendo `Number`s, `String`s, `Symbol`s, `Type`s, `Function`s y algunos singleton comunes como [`missing`](@ref) y [`nothing`](@ref). Todos los demás argumentos se iteran o se indexan de manera elementwise.

El tipo de contenedor resultante se establece mediante las siguientes reglas:

  * Si todos los argumentos son escalares o arreglos de cero dimensiones, devuelve un escalar sin envolver.
  * Si al menos un argumento es una tupla y todos los demás son escalares o arreglos de cero dimensiones, devuelve una tupla.
  * Todas las demás combinaciones de argumentos por defecto devuelven un `Array`, pero los tipos de contenedores personalizados pueden definir su propia implementación y reglas de promoción para personalizar el resultado cuando aparecen como argumentos.

Existe una sintaxis especial para la difusión: `f.(args...)` es equivalente a `broadcast(f, args...)`, y las llamadas anidadas `f.(g.(args...))` se fusionan en un solo bucle de difusión.

# Ejemplos

```jldoctest
julia> A = [1, 2, 3, 4, 5]
5-element Vector{Int64}:
 1
 2
 3
 4
 5

julia> B = [1 2; 3 4; 5 6; 7 8; 9 10]
5×2 Matrix{Int64}:
 1   2
 3   4
 5   6
 7   8
 9  10

julia> broadcast(+, A, B)
5×2 Matrix{Int64}:
  2   3
  5   6
  8   9
 11  12
 14  15

julia> parse.(Int, ["1", "2"])
2-element Vector{Int64}:
 1
 2

julia> abs.((1, -2))
(1, 2)

julia> broadcast(+, 1.0, (0, -2.0))
(1.0, -1.0)

julia> (+).([[0,2], [1,3]], Ref{Vector{Int}}([1,-1]))
2-element Vector{Vector{Int64}}:
 [1, 1]
 [2, 2]

julia> string.(("one","two","three","four"), ": ", 1:4)
4-element Vector{String}:
 "one: 1"
 "two: 2"
 "three: 3"
 "four: 4"

```
