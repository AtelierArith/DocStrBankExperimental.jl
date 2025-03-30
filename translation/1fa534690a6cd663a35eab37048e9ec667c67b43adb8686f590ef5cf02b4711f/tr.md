```
log2(x)
```

`x` için 2 tabanında logaritmayı hesaplar. Negatif [`Real`](@ref) argümanlar için [`DomainError`](@ref) fırlatır.

Ayrıca bakınız: [`exp2`](@ref), [`ldexp`](@ref), [`ispow2`](@ref).

# Örnekler

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> log2(4)
2.0

julia> log2(10)
3.321928094887362

julia> log2(-2)
HATA: DomainError ile -2.0:
log2 negatif bir gerçek argüman ile çağrıldı ancak yalnızca karmaşık bir argüman ile çağrıldığında karmaşık bir sonuç döndürecektir. log2(Complex(x))'i deneyin.
Stacktrace:
 [1] throw_complex_domainerror(f::Symbol, x::Float64) at ./math.jl:31
[...]

julia> log2.(2.0 .^ (-1:1))
3-element Vector{Float64}:
 -1.0
  0.0
  1.0
```
