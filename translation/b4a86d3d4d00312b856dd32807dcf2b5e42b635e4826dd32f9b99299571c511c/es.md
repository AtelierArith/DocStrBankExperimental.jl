```
hessenberg(A) -> Hessenberg
```

Calcula la descomposición de Hessenberg de `A` y devuelve un objeto `Hessenberg`. Si `F` es el objeto de factorización, la matriz unitaria se puede acceder con `F.Q` (de tipo `LinearAlgebra.HessenbergQ`) y la matriz de Hessenberg con `F.H` (de tipo [`UpperHessenberg`](@ref)), cualquiera de las cuales puede ser convertida a una matriz regular con `Matrix(F.H)` o `Matrix(F.Q)`.

Si `A` es [`Hermitiana`](@ref) o real-[`Simétrica`](@ref), entonces la descomposición de Hessenberg produce una matriz tridiagonal real-simétrica y `F.H` es de tipo [`SymTridiagonal`](@ref).

Ten en cuenta que la factorización desplazada `A+μI = Q (H+μI) Q'` se puede construir de manera eficiente mediante `F + μ*I` usando el objeto [`UniformScaling`](@ref) [`I`](@ref), que crea un nuevo objeto `Hessenberg` con almacenamiento compartido y un desplazamiento modificado. El desplazamiento de un dado `F` se obtiene mediante `F.μ`. Esto es útil porque múltiples resoluciones desplazadas `(F + μ*I) \ b` (para diferentes `μ` y/o `b`) se pueden realizar de manera eficiente una vez que se crea `F`.

Iterar la descomposición produce los factores `F.Q, F.H, F.μ`.

# Ejemplos

```julia-repl
julia> A = [4. 9. 7.; 4. 4. 1.; 4. 3. 2.]
3×3 Matrix{Float64}:
 4.0  9.0  7.0
 4.0  4.0  1.0
 4.0  3.0  2.0

julia> F = hessenberg(A)
Hessenberg{Float64, UpperHessenberg{Float64, Matrix{Float64}}, Matrix{Float64}, Vector{Float64}, Bool}
Q factor: 3×3 LinearAlgebra.HessenbergQ{Float64, Matrix{Float64}, Vector{Float64}, false}
H factor:
3×3 UpperHessenberg{Float64, Matrix{Float64}}:
  4.0      -11.3137       -1.41421
 -5.65685    5.0           2.0
   ⋅        -8.88178e-16   1.0

julia> F.Q * F.H * F.Q'
3×3 Matrix{Float64}:
 4.0  9.0  7.0
 4.0  4.0  1.0
 4.0  3.0  2.0

julia> q, h = F; # desestructuración mediante iteración

julia> q == F.Q && h == F.H
true
```
