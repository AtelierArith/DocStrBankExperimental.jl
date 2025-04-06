```
Bidiagonal(dv::V, ev::V, uplo::Symbol) donde V <: AbstractVector
```

Construye una matriz bidiagonal superior (`uplo=:U`) o inferior (`uplo=:L`) utilizando los vectores diagonales dados (`dv`) y off-diagonales (`ev`). El resultado es de tipo `Bidiagonal` y proporciona solucionadores lineales especializados eficientes, pero puede ser convertido en una matriz regular con [`convert(Array, _)`](@ref) (o `Array(_)` para abreviar). La longitud de `ev` debe ser una menos que la longitud de `dv`.

# Ejemplos

```jldoctest
julia> dv = [1, 2, 3, 4]
4-element Vector{Int64}:
 1
 2
 3
 4

julia> ev = [7, 8, 9]
3-element Vector{Int64}:
 7
 8
 9

julia> Bu = Bidiagonal(dv, ev, :U) # ev está en la primera superdiagonal
4×4 Bidiagonal{Int64, Vector{Int64}}:
 1  7  ⋅  ⋅
 ⋅  2  8  ⋅
 ⋅  ⋅  3  9
 ⋅  ⋅  ⋅  4

julia> Bl = Bidiagonal(dv, ev, :L) # ev está en la primera subdiagonal
4×4 Bidiagonal{Int64, Vector{Int64}}:
 1  ⋅  ⋅  ⋅
 7  2  ⋅  ⋅
 ⋅  8  3  ⋅
 ⋅  ⋅  9  4
```
