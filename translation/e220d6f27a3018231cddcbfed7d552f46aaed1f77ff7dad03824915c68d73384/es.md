```
El operador "splat", `...`, representa una secuencia de argumentos. `...` se puede usar en definiciones de funciones, para indicar que la función acepta un número arbitrario de argumentos. `...` también se puede usar para aplicar una función a una secuencia de argumentos.

# Ejemplos

```

jldoctest julia> add(xs...) = reduce(+, xs) add (generic function with 1 method)

julia> add(1, 2, 3, 4, 5) 15

julia> add([1, 2, 3]...) 6

julia> add(7, 1:100..., 1000:1100...) 111107

```

```
