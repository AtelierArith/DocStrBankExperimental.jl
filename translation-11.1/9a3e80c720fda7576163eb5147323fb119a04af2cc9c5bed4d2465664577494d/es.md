```
eps(x::AbstractFloat)
```

Devuelve la *unidad en la última posición* (ulp) de `x`. Esta es la distancia entre los valores de punto flotante representables consecutivos en `x`. En la mayoría de los casos, si la distancia a cada lado de `x` es diferente, se toma el mayor de los dos, es decir,

```
eps(x) == max(x-prevfloat(x), nextfloat(x)-x)
```

Las excepciones a esta regla son los valores finitos más pequeños y más grandes (por ejemplo, `nextfloat(-Inf)` y `prevfloat(Inf)` para [`Float64`](@ref)), que redondean al menor de los valores.

La razón de este comportamiento es que `eps` limita el error de redondeo de punto flotante. Bajo el modo de redondeo predeterminado `RoundNearest`, si $y$ es un número real y $x$ es el número de punto flotante más cercano a $y$, entonces

$$
|y-x| \leq \operatorname{eps}(x)/2.
$$

Véase también: [`nextfloat`](@ref), [`issubnormal`](@ref), [`floatmax`](@ref).

# Ejemplos

```jldoctest
julia> eps(1.0)
2.220446049250313e-16

julia> eps(prevfloat(2.0))
2.220446049250313e-16

julia> eps(2.0)
4.440892098500626e-16

julia> x = prevfloat(Inf)      # mayor Float64 finito
1.7976931348623157e308

julia> x + eps(x)/2            # redondea hacia arriba
Inf

julia> x + prevfloat(eps(x)/2) # redondea hacia abajo
1.7976931348623157e308
```
