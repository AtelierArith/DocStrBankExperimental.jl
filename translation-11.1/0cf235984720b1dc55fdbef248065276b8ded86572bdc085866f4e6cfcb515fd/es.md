```
ldlt(A::SparseMatrixCSC; shift = 0.0, check = true, perm=nothing) -> CHOLMOD.Factor
```

Calcula la factorización $LDL'$ de una matriz dispersa `A`. `A` debe ser una [`SparseMatrixCSC`](@ref) o una vista [`Symmetric`](@ref)/[`Hermitian`](@ref) de una `SparseMatrixCSC`. Ten en cuenta que, incluso si `A` no tiene la etiqueta de tipo, aún debe ser simétrica o hermítica. Se utiliza una permutación que reduce el llenado. `F = ldlt(A)` se usa con mayor frecuencia para resolver sistemas de ecuaciones `A*x = b` con `F\b`. El objeto de factorización devuelto `F` también admite los métodos [`diag`](@ref), [`det`](@ref), [`logdet`](@ref) y [`inv`](@ref). Puedes extraer factores individuales de `F` usando `F.L`. Sin embargo, dado que el pivoteo está activado por defecto, la factorización se representa internamente como `A == P'*L*D*L'*P` con una matriz de permutación `P`; usar solo `L` sin tener en cuenta `P` dará respuestas incorrectas. Para incluir los efectos de la permutación, generalmente es preferible extraer factores "combinados" como `PtL = F.PtL` (el equivalente de `P'*L`) y `LtP = F.UP` (el equivalente de `L'*P`). La lista completa de factores admitidos es `:L, :PtL, :D, :UP, :U, :LD, :DU, :PtLD, :DUP`.

Cuando `check = true`, se lanza un error si la descomposición falla. Cuando `check = false`, la responsabilidad de verificar la validez de la descomposición (a través de [`issuccess`](@ref)) recae en el usuario.

Establecer el argumento de palabra clave opcional `shift` calcula la factorización de `A+shift*I` en lugar de `A`. Si se proporciona el argumento `perm`, debe ser una permutación de `1:size(A,1)` que da el orden a utilizar (en lugar del orden predeterminado AMD de CHOLMOD).

!!! nota
    Este método utiliza la biblioteca CHOLMOD[^ACM887][^DavisHager2009] de [SuiteSparse](https://github.com/DrTimothyAldenDavis/SuiteSparse). CHOLMOD solo admite tipos reales o complejos en precisión simple o doble. Las matrices de entrada que no son de esos tipos de elementos se convertirán a estos tipos según sea apropiado.

    Muchas otras funciones de CHOLMOD están envueltas pero no exportadas del módulo `Base.SparseArrays.CHOLMOD`.

