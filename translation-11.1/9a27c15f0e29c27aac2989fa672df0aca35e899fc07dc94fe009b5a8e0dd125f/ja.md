```
log1p(x)
```

`1+x`の正確な自然対数。`-1`未満の[`Real`](@ref)引数に対しては[`DomainError`](@ref)をスローします。

# 例

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> log1p(-0.5)
-0.6931471805599453

julia> log1p(0)
0.0

julia> log1p(-2)
ERROR: DomainError with -2.0:
log1pは実引数が<-1で呼び出されましたが、複素引数で呼び出された場合にのみ複素結果を返します。log1p(Complex(x))を試してください。
Stacktrace:
 [1] throw_complex_domainerror(::Symbol, ::Float64) at ./math.jl:31
[...]
```
