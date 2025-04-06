```
Float32 <: AbstractFloat <: Real
```

Type de nombre à virgule flottante 32 bits (norme IEEE 754). Le format binaire est 1 signe, 8 exposants, 23 bits de fraction.

L'exposant pour la notation scientifique doit être saisi en minuscules `f`, donc `2f3 === 2.0f0 * 10^3 === Float32(2_000)`. Pour les littéraux de tableau et les compréhensions, le type d'élément peut être spécifié avant les crochets : `Float32[1,4,9] == Float32[i^2 for i in 1:3]`.

Voir aussi [`Inf32`](@ref), [`NaN32`](@ref), [`Float16`](@ref), [`exponent`](@ref), [`frexp`](@ref).
