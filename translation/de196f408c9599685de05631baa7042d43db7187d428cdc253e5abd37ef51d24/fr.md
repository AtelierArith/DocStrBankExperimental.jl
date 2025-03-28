```
Float64 <: AbstractFloat <: Real
```

Type de nombre à virgule flottante 64 bits (norme IEEE 754). Le format binaire est 1 bit de signe, 11 bits d'exposant, 52 bits de fraction. Voir [`bitstring`](@ref), [`signbit`](@ref), [`exponent`](@ref), [`frexp`](@ref), et [`significand`](@ref) pour accéder à divers bits.

C'est le type par défaut pour les littéraux à virgule flottante, `1.0 isa Float64`, et pour de nombreuses opérations telles que `1/2, 2pi, log(2), range(0,90,length=4)`. Contrairement aux entiers, ce type par défaut ne change pas avec `Sys.WORD_SIZE`.

L'exposant pour la notation scientifique peut être saisi sous la forme `e` ou `E`, donc `2e3 === 2.0E3 === 2.0 * 10^3`. Il est fortement recommandé de le faire plutôt que d'utiliser `10^n` car les entiers peuvent déborder, donc `2.0 * 10^19 < 0` mais `2e19 > 0`.

Voir aussi [`Inf`](@ref), [`NaN`](@ref), [`floatmax`](@ref), [`Float32`](@ref), [`Complex`](@ref).
