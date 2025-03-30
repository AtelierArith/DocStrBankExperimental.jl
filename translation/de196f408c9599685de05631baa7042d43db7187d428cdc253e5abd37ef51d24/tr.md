```
Float64 <: AbstractFloat <: Real
```

64-bit kayan nokta sayısı türü (IEEE 754 standardı). İkili format 1 işaret, 11 üs, 52 kesir bitidir. Çeşitli bitlere erişmek için [`bitstring`](@ref), [`signbit`](@ref), [`exponent`](@ref), [`frexp`](@ref) ve [`significand`](@ref) bakın.

Bu, kayan nokta literalleri için varsayılan olanıdır, `1.0 isa Float64` ve `1/2, 2pi, log(2), range(0,90,length=4)` gibi birçok işlem için. Tam sayılardan farklı olarak, bu varsayılan `Sys.WORD_SIZE` ile değişmez.

Bilimsel notasyon için üs `e` veya `E` olarak girilebilir, böylece `2e3 === 2.0E3 === 2.0 * 10^3`. Bunu `10^n` yerine kullanmak şiddetle tercih edilir çünkü tam sayılar taşar, bu nedenle `2.0 * 10^19 < 0` ama `2e19 > 0`.

Ayrıca [`Inf`](@ref), [`NaN`](@ref), [`floatmax`](@ref), [`Float32`](@ref), [`Complex`](@ref) bakın.
