```
log1p(x)
```

`1+x`'in doğal logaritmasını doğru bir şekilde hesaplar. [`Real`](@ref) argümanları -1'den küçük olduğunda [`DomainError`](@ref) fırlatır.

# Örnekler

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> log1p(-0.5)
-0.6931471805599453

julia> log1p(0)
0.0

julia> log1p(-2)
HATA: -2.0 ile DomainError:
log1p, -1'den küçük bir gerçek argüman ile çağrıldı ancak yalnızca karmaşık bir argüman ile çağrıldığında karmaşık bir sonuç döndürecektir. log1p(Complex(x))'i deneyin.
Stacktrace:
 [1] throw_complex_domainerror(::Symbol, ::Float64) at ./math.jl:31
[...]
```
