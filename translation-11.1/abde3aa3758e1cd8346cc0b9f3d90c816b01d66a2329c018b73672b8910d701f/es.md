```
lu(A::AbstractSparseMatrixCSC; check = true, q = nothing, control = get_umfpack_control()) -> F::UmfpackLU
```

Calcula la factorización LU de una matriz dispersa `A`.

Para `A` dispersa con tipo de elemento real o complejo, el tipo de retorno de `F` es `UmfpackLU{Tv, Ti}`, donde `Tv` = [`Float64`](@ref) o `ComplexF64` respectivamente y `Ti` es un tipo entero ([`Int32`](@ref) o [`Int64`](@ref)).

Cuando `check = true`, se lanza un error si la descomposición falla. Cuando `check = false`, la responsabilidad de verificar la validez de la descomposición (a través de [`issuccess`](@ref)) recae en el usuario.

El vector de permutación `q` puede ser un vector de permutación o `nothing`. Si no se proporciona un vector de permutación o `q` es `nothing`, se utiliza el predeterminado de UMFPACK. Si la permutación no es basada en cero, se realiza una copia basada en cero.

El vector `control` tiene como configuración predeterminada la configuración predeterminada del paquete SparseArrays de Julia para UMFPACK (NB: esto se modifica de los predeterminados de UMFPACK para deshabilitar el refinamiento iterativo), pero se puede cambiar pasando un vector de longitud `UMFPACK_CONTROL`, consulta el manual de UMFPACK para posibles configuraciones. Por ejemplo, para reactivar el refinamiento iterativo:

```
umfpack_control = SparseArrays.UMFPACK.get_umfpack_control(Float64, Int64) # leer la configuración predeterminada de Julia para una matriz dispersa Float64
SparseArrays.UMFPACK.show_umf_ctrl(umfpack_control) # opcional - mostrar valores
umfpack_control[SparseArrays.UMFPACK.JL_UMFPACK_IRSTEP] = 2.0 # reactivar el refinamiento iterativo (2 es el máximo de pasos de refinamiento iterativo predeterminado de UMFPACK)

Alu = lu(A; control = umfpack_control)
x = Alu \ b   # resolver Ax = b, incluyendo el refinamiento iterativo de UMFPACK
```

Los componentes individuales de la factorización `F` se pueden acceder mediante indexación:

| Componente | Descripción                             |
|:---------- |:--------------------------------------- |
| `L`        | parte `L` (triangular inferior) de `LU` |
| `U`        | parte `U` (triangular superior) de `LU` |
| `p`        | permutación derecha `Vector`            |
| `q`        | permutación izquierda `Vector`          |
| `Rs`       | `Vector` de factores de escalado        |
| `:`        | componentes `(L,U,p,q,Rs)`              |

La relación entre `F` y `A` es

`F.L*F.U == (F.Rs .* A)[F.p, F.q]`

`F` además soporta las siguientes funciones:

  * [`\`](@ref)
  * [`det`](@ref)

Consulta también [`lu!`](@ref)

!!! nota
    `lu(A::AbstractSparseMatrixCSC)` utiliza la biblioteca UMFPACK[^ACM832] que es parte de [SuiteSparse](https://github.com/DrTimothyAldenDavis/SuiteSparse). Como esta biblioteca solo admite matrices dispersas con elementos [`Float64`](@ref) o `ComplexF64`, `lu` convierte `A` en una copia que es de tipo `SparseMatrixCSC{Float64}` o `SparseMatrixCSC{ComplexF64}` según corresponda.


[^ACM832]: Davis, Timothy A. (2004b). Algorithm 832: UMFPACK V4.3–-an Unsymmetric-Pattern Multifrontal Method. ACM Trans. Math. Softw., 30(2), 196–199. [doi:10.1145/992200.992206](https://doi.org/10.1145/992200.992206)
