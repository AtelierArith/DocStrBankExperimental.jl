```
lu!(F::UmfpackLU, A::AbstractSparseMatrixCSC; check=true, reuse_symbolic=true, q=nothing) -> F::UmfpackLU
```

Calcula la factorización LU de una matriz dispersa `A`, reutilizando la factorización simbólica de una factorización LU ya existente almacenada en `F`. A menos que `reuse_symbolic` se establezca en falso, la matriz dispersa `A` debe tener un patrón de no ceros idéntico al de la matriz utilizada para crear la factorización LU `F`, de lo contrario se lanzará un error. Si el tamaño de `A` y `F` difiere, todos los vectores se redimensionarán en consecuencia.

Cuando `check = true`, se lanza un error si la descomposición falla. Cuando `check = false`, la responsabilidad de verificar la validez de la descomposición (a través de [`issuccess`](@ref)) recae en el usuario.

La permutación `q` puede ser un vector de permutación o `nothing`. Si no se proporciona un vector de permutación o `q` es `nothing`, se utiliza el valor predeterminado de UMFPACK. Si la permutación no es basada en cero, se realiza una copia basada en cero.

Véase también [`lu`](@ref)

!!! note
    `lu!(F::UmfpackLU, A::AbstractSparseMatrixCSC)` utiliza la biblioteca UMFPACK que es parte de SuiteSparse. Como esta biblioteca solo admite matrices dispersas con elementos de [`Float64`](@ref) o `ComplexF64`, `lu!` convertirá automáticamente los tipos a aquellos establecidos por la factorización LU o `SparseMatrixCSC{ComplexF64}` según corresponda.


!!! compat "Julia 1.5"
    `lu!` para `UmfpackLU` requiere al menos Julia 1.5.


# Ejemplos

```jldoctest
julia> A = sparse(Float64[1.0 2.0; 0.0 3.0]);

julia> F = lu(A);

julia> B = sparse(Float64[1.0 1.0; 0.0 1.0]);

julia> lu!(F, B);

julia> F \ ones(2)
2-element Vector{Float64}:
 0.0
 1.0
```
