```
log10(x)
```

`x` için 10 tabanında logaritmayı hesaplar. Negatif [`Real`](@ref) argümanlar için [`DomainError`](@ref) fırlatır.

# Örnekler

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> log10(100)
2.0

julia> log10(2)
0.3010299956639812

julia> log10(-2)
HATA: -2.0 ile DomainError:
log10 negatif bir gerçek argüman ile çağrıldı, ancak yalnızca karmaşık bir argüman ile çağrıldığında karmaşık bir sonuç döndürecektir. log10(Complex(x)) deneyin.
Stacktrace:
 [1] throw_complex_domainerror(f::Symbol, x::Float64) at ./math.jl:31
[...]
```
