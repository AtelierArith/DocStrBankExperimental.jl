```
Meta.quot(ex)::Expr
```

İfadenin `ex` alıntısını alarak `quote` başlığına sahip bir ifade üretir. Bu, örneğin, AST'deki `Expr` türündeki nesneleri temsil etmek için kullanılabilir. Ayrıca [QuoteNode](@ref man-quote-node) hakkında kılavuz bölümüne de bakın.

# Örnekler

```jldoctest
julia> eval(Meta.quot(:x))
:x

julia> dump(Meta.quot(:x))
Expr
  head: Symbol quote
  args: Array{Any}((1,))
    1: Symbol x

julia> eval(Meta.quot(:(1+2)))
:(1 + 2)
```
