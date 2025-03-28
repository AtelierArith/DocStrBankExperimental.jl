```
eigen(A; permute::Bool=true, scale::Bool=true, sortby) -> Eigen
```

Calcula la descomposición en valores propios de `A`, devolviendo un objeto de factorización [`Eigen`](@ref) `F` que contiene los valores propios en `F.values` y los vectores propios en las columnas de la matriz `F.vectors`. Esto corresponde a resolver un problema de valores propios de la forma `Ax =  λx`, donde `A` es una matriz, `x` es un vector propio, y `λ` es un valor propio. (El `k`-ésimo vector propio se puede obtener de la porción `F.vectors[:, k]`.)

Iterar la descomposición produce los componentes `F.values` y `F.vectors`.

Las siguientes funciones están disponibles para los objetos `Eigen`: [`inv`](@ref), [`det`](@ref), y [`isposdef`](@ref).

Para matrices generales no simétricas, es posible especificar cómo se balancea la matriz antes del cálculo del vector propio. La opción `permute=true` permuta la matriz para acercarse a una forma triangular superior, y `scale=true` escala la matriz por sus elementos diagonales para hacer que las filas y columnas sean más iguales en norma. El valor predeterminado es `true` para ambas opciones.

Por defecto, los valores y vectores propios se ordenan lexicográficamente por `(real(λ),imag(λ))`. Se puede pasar una función de comparación diferente `by(λ)` a `sortby`, o se puede pasar `sortby=nothing` para dejar los valores propios en un orden arbitrario. Algunos tipos de matriz especiales (por ejemplo, [`Diagonal`](@ref) o [`SymTridiagonal`](@ref)) pueden implementar su propia convención de ordenación y no aceptar una palabra clave `sortby`.

# Ejemplos

```jldoctest
julia> F = eigen([1.0 0.0 0.0; 0.0 3.0 0.0; 0.0 0.0 18.0])
Eigen{Float64, Float64, Matrix{Float64}, Vector{Float64}}
values:
3-element Vector{Float64}:
  1.0
  3.0
 18.0
vectors:
3×3 Matrix{Float64}:
 1.0  0.0  0.0
 0.0  1.0  0.0
 0.0  0.0  1.0

julia> F.values
3-element Vector{Float64}:
  1.0
  3.0
 18.0

julia> F.vectors
3×3 Matrix{Float64}:
 1.0  0.0  0.0
 0.0  1.0  0.0
 0.0  0.0  1.0

julia> vals, vecs = F; # destructuring via iteration

julia> vals == F.values && vecs == F.vectors
true
```
