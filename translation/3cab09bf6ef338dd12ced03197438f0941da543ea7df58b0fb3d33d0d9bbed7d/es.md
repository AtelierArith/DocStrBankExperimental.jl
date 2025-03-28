```
rank(A::AbstractMatrix; atol::Real=0, rtol::Real=atol>0 ? 0 : n*ϵ)
rank(A::AbstractMatrix, rtol::Real)
```

Calcula el rango numérico de una matriz contando cuántos valores de salida de `svdvals(A)` son mayores que `max(atol, rtol*σ₁)`, donde `σ₁` es el valor singular más grande calculado de `A`. `atol` y `rtol` son las tolerancias absolutas y relativas, respectivamente. La tolerancia relativa por defecto es `n*ϵ`, donde `n` es el tamaño de la dimensión más pequeña de `A`, y `ϵ` es el [`eps`](@ref) del tipo de elemento de `A`.

!!! note
    El rango numérico puede ser una caracterización sensible e imprecisa de matrices mal condicionadas con valores singulares que están cerca de la tolerancia umbral `max(atol, rtol*σ₁)`. En tales casos, ligeras perturbaciones en el cálculo del valor singular o en la matriz pueden cambiar el resultado de `rank` al empujar uno o más valores singulares a través del umbral. Estas variaciones pueden incluso ocurrir debido a cambios en errores de punto flotante entre diferentes versiones de Julia, arquitecturas, compiladores o sistemas operativos.


!!! compat "Julia 1.1"
    Los argumentos de palabra clave `atol` y `rtol` requieren al menos Julia 1.1. En Julia 1.0, `rtol` está disponible como un argumento posicional, pero esto será desaprobado en Julia 2.0.


# Ejemplos

```jldoctest
julia> rank(Matrix(I, 3, 3))
3

julia> rank(diagm(0 => [1, 0, 2]))
2

julia> rank(diagm(0 => [1, 0.001, 2]), rtol=0.1)
2

julia> rank(diagm(0 => [1, 0.001, 2]), rtol=0.00001)
3

julia> rank(diagm(0 => [1, 0.001, 2]), atol=1.5)
1
```
