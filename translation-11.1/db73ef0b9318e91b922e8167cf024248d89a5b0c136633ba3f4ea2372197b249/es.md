```
eigen(A::Union{SymTridiagonal, Hermitian, Symmetric}, irange::UnitRange) -> Eigen
```

Calcula la descomposición en valores propios de `A`, devolviendo un objeto de factorización [`Eigen`](@ref) `F` que contiene los valores propios en `F.values` y los vectores propios en las columnas de la matriz `F.vectors`. (El `k`-ésimo vector propio se puede obtener de la porción `F.vectors[:, k]`.)

Iterar la descomposición produce los componentes `F.values` y `F.vectors`.

Las siguientes funciones están disponibles para los objetos `Eigen`: [`inv`](@ref), [`det`](@ref), y [`isposdef`](@ref).

El [`UnitRange`](@ref) `irange` especifica los índices de los valores propios ordenados a buscar.

!!! note
    Si `irange` no es `1:n`, donde `n` es la dimensión de `A`, entonces la factorización devuelta será una factorización *truncada*.

