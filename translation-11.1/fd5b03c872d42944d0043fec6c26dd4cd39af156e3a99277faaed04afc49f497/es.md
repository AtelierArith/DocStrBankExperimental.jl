```
Float32 <: AbstractFloat <: Real
```

Tipo de número de punto flotante de 32 bits (estándar IEEE 754). El formato binario es 1 signo, 8 exponentes, 23 bits de fracción.

El exponente para la notación científica debe ingresarse como `f` en minúscula, así `2f3 === 2.0f0 * 10^3 === Float32(2_000)`. Para literales de arreglos y comprensiones, el tipo de elemento se puede especificar antes de los corchetes: `Float32[1,4,9] == Float32[i^2 for i in 1:3]`.

Véase también [`Inf32`](@ref), [`NaN32`](@ref), [`Float16`](@ref), [`exponent`](@ref), [`frexp`](@ref).
