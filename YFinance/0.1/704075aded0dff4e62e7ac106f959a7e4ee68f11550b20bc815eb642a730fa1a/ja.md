```
get_valid_symbols(symbol::AbstractString)
```

シンボルを取得します。シンボルが有効な場合は、シンボルをベクターで返し、無効な場合は空のベクターを返します。

# 引数

  * `smybol::AbstractString` はティッカー（例：Apple ComputersのAAPL、またはS&P500の^GSPC）です。

# 例

```julia-repl
julia> get_valid_symbols("AAPL")
1-element Vector{String}:
 "AAPL"

julia> get_valid_symbols("asdfs")
 String[]
```
