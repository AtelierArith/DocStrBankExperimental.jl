```
Float64 <: AbstractFloat <: Real
```

Tipo de número de punto flotante de 64 bits (estándar IEEE 754). El formato binario es 1 signo, 11 exponentes, 52 bits de fracción. Consulte [`bitstring`](@ref), [`signbit`](@ref), [`exponent`](@ref), [`frexp`](@ref) y [`significand`](@ref) para acceder a varios bits.

Este es el valor predeterminado para literales de punto flotante, `1.0 isa Float64`, y para muchas operaciones como `1/2, 2pi, log(2), range(0,90,length=4)`. A diferencia de los enteros, este valor predeterminado no cambia con `Sys.WORD_SIZE`.

El exponente para la notación científica se puede ingresar como `e` o `E`, por lo tanto `2e3 === 2.0E3 === 2.0 * 10^3`. Hacerlo se prefiere fuertemente sobre `10^n` porque los enteros desbordarán, por lo tanto `2.0 * 10^19 < 0` pero `2e19 > 0`.

Consulte también [`Inf`](@ref), [`NaN`](@ref), [`floatmax`](@ref), [`Float32`](@ref), [`Complex`](@ref).
