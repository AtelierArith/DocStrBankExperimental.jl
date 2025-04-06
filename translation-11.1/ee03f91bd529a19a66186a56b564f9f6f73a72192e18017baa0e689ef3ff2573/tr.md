```
√(x)
```

Sonuç $\sqrt{x}$.

Negatif [`Real`](@ref) argümanlar için [`DomainError`](@ref) fırlatır. Bunun yerine karmaşık negatif argümanlar kullanın. `sqrt`'ın negatif reel eksen boyunca bir dal kesimi olduğunu unutmayın.

Önek operatör `√`, `sqrt` ile eşdeğerdir.

Ayrıca bkz: [`hypot`](@ref).

# Örnekler

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> sqrt(big(81))
9.0

julia> sqrt(big(-81))
HATA: -81.0 ile DomainError:
NaN girişi için NaN olmayan sonuç.
Stacktrace:
 [1] sqrt(::BigFloat) at ./mpfr.jl:501
[...]

julia> sqrt(big(complex(-81)))
0.0 + 9.0im

julia> sqrt(-81 - 0.0im)  # -0.0im dal kesiminin altında
0.0 - 9.0im

julia> .√(1:4)
4-element Vector{Float64}:
 1.0
 1.4142135623730951
 1.7320508075688772
 2.0
```
