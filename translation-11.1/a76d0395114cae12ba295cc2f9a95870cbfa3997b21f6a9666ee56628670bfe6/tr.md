```
:expr
```

Bir ifadeyi `expr` alıntılayın ve `expr`'nin soyut sözdizim ağacını (AST) döndürün. AST, `Expr`, `Symbol` veya bir literal değer türünde olabilir. `:identifier` sözdizimi bir `Symbol`'a değerlenecektir.

Ayrıca bakınız: [`Expr`](@ref), [`Symbol`](@ref), [`Meta.parse`](@ref)

# Örnekler

```jldoctest
julia> expr = :(a = b + 2*x)
:(a = b + 2x)

julia> sym = :some_identifier
:some_identifier

julia> value = :0xff
0xff

julia> typeof((expr, sym, value))
Tuple{Expr, Symbol, UInt8}
```
