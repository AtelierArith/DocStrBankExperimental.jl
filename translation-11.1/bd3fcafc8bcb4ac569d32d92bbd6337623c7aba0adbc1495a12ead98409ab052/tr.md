```
Expr(head::Symbol, args...)
```

Parçalanmış julia kodundaki (AST'ler) bileşik ifadeleri temsil eden bir tür. Her ifade, hangi tür ifade olduğunu belirten bir `head` `Symbol`'ü (örneğin bir çağrı, for döngüsü, koşullu ifade vb.) ve alt ifadeleri (örneğin bir çağrının argümanları) içerir. Alt ifadeler, `args` adında bir `Vector{Any}` alanında saklanır.

[Metaprogramming](@ref) konusundaki kılavuz bölümüne ve geliştirici belgelerine [Julia ASTs](@ref) bakın.

# Örnekler

```jldoctest
julia> Expr(:call, :+, 1, 2)
:(1 + 2)

julia> dump(:(a ? b : c))
Expr
  head: Symbol if
  args: Array{Any}((3,))
    1: Symbol a
    2: Symbol b
    3: Symbol c
```
