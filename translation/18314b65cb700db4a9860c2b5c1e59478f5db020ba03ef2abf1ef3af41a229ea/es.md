```
fill(value, dims::Tuple)
fill(value, dims...)
```

Crea un arreglo de tamaño `dims` con cada ubicación establecida en `value`.

Por ejemplo, `fill(1.0, (5,5))` devuelve un arreglo de 5×5 de flotantes, con `1.0` en cada ubicación del arreglo.

Las longitudes de las dimensiones `dims` pueden especificarse como una tupla o como una secuencia de argumentos. Una tupla de longitud `N` o `N` argumentos después de `value` especifican un arreglo de `N` dimensiones. Así, un idiom común para crear un arreglo de cero dimensiones con su única ubicación establecida en `x` es `fill(x)`.

Cada ubicación del arreglo devuelto se establece en (y es por lo tanto [`===`](@ref) a) el `value` que se pasó; esto significa que si el `value` se modifica, todos los elementos del arreglo `fill`ado reflejarán esa modificación porque *siguen siendo* ese mismo `value`. Esto no es un problema con `fill(1.0, (5,5))` ya que el `value` `1.0` es inmutable y no puede ser modificado, pero puede ser inesperado con valores mutables como — más comúnmente — arreglos. Por ejemplo, `fill([], 3)` coloca *el mismo* arreglo vacío en las tres ubicaciones del vector devuelto:

```jldoctest
julia> v = fill([], 3)
3-element Vector{Vector{Any}}:
 []
 []
 []

julia> v[1] === v[2] === v[3]
true

julia> value = v[1]
Any[]

julia> push!(value, 867_5309)
1-element Vector{Any}:
 8675309

julia> v
3-element Vector{Vector{Any}}:
 [8675309]
 [8675309]
 [8675309]
```

Para crear un arreglo de muchos arreglos internos independientes, usa una [comprensión](@ref man-comprehensions) en su lugar. Esto crea un nuevo y distinto arreglo en cada iteración del bucle:

```jldoctest
julia> v2 = [[] for _ in 1:3]
3-element Vector{Vector{Any}}:
 []
 []
 []

julia> v2[1] === v2[2] === v2[3]
false

julia> push!(v2[1], 8675309)
1-element Vector{Any}:
 8675309

julia> v2
3-element Vector{Vector{Any}}:
 [8675309]
 []
 []
```

Ver también: [`fill!`](@ref), [`zeros`](@ref), [`ones`](@ref), [`similar`](@ref).

# Ejemplos

```jldoctest
julia> fill(1.0, (2,3))
2×3 Matrix{Float64}:
 1.0  1.0  1.0
 1.0  1.0  1.0

julia> fill(42)
0-dimensional Array{Int64, 0}:
42

julia> A = fill(zeros(2), 2) # establece ambos elementos en el mismo vector [0.0, 0.0]
2-element Vector{Vector{Float64}}:
 [0.0, 0.0]
 [0.0, 0.0]

julia> A[1][1] = 42; # modifica el valor llenado a ser [42.0, 0.0]

julia> A # tanto A[1] como A[2] son el mismo vector
2-element Vector{Vector{Float64}}:
 [42.0, 0.0]
 [42.0, 0.0]
```
