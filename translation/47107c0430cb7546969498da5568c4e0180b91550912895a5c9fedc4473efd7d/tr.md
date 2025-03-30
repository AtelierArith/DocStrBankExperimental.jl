```
log(x)
```

`x`'in doğal logaritmasını hesaplar.

Negatif [`Real`](@ref) argümanlar için [`DomainError`](@ref) fırlatır. Karmaşık sonuçlar elde etmek için karmaşık argümanlar kullanın. Negatif reel eksen boyunca bir dal kesimi vardır; bu eksenin altında `-0.0im` alınır.

Ayrıca bkz. [`ℯ`](@ref), [`log1p`](@ref), [`log2`](@ref), [`log10`](@ref).

# Örnekler

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> log(2)
0.6931471805599453

julia> log(-3)
HATA: DomainError with -3.0:
log negatif reel bir argüman ile çağrıldı ancak yalnızca karmaşık bir argüman ile çağrıldığında karmaşık bir sonuç döndürecektir. log(Complex(x))'i deneyin.
Stacktrace:
 [1] throw_complex_domainerror(::Symbol, ::Float64) at ./math.jl:31
[...]

julia> log(-3 + 0im)
1.0986122886681098 + 3.141592653589793im

julia> log(-3 - 0.0im)
1.0986122886681098 - 3.141592653589793im

julia> log.(exp.(-1:1))
3-element Vector{Float64}:
 -1.0
  0.0
  1.0
```
