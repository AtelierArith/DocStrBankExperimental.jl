```
mod(x, y)
rem(x, y, RoundDown)
```

La reducción de `x` módulo `y`, o equivalentemente, el residuo de `x` después de la división redondeada hacia abajo por `y`, es decir, `x - y*fld(x,y)` si se calcula sin redondeo intermedio.

El resultado tendrá el mismo signo que `y`, y una magnitud menor que `abs(y)` (con algunas excepciones, ver la nota a continuación).

!!! nota
    Cuando se utiliza con valores de punto flotante, el resultado exacto puede no ser representable por el tipo, y por lo tanto puede ocurrir un error de redondeo. En particular, si el resultado exacto está muy cerca de `y`, entonces puede redondearse a `y`.


Véase también: [`rem`](@ref), [`div`](@ref), [`fld`](@ref), [`mod1`](@ref), [`invmod`](@ref).

```jldoctest
julia> mod(8, 3)
2

julia> mod(9, 3)
0

julia> mod(8.9, 3)
2.9000000000000004

julia> mod(eps(), 3)
2.220446049250313e-16

julia> mod(-eps(), 3)
3.0

julia> mod.(-5:5, 3)'
1×11 adjoint(::Vector{Int64}) with eltype Int64:
 1  2  0  1  2  0  1  2  0  1  2
```
