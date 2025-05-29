```
get_valid_symbols(symbol::AbstractVector{<:AbstractString})
```

`AbstractVector` のシンボルを受け取り、有効なものだけを返します。

# 引数

  * `smybol::AbstractVector{<:AbstractString}` はティッカーのベクターです（例：Apple Computers の AAPL、または S&P500 の ^GSPC）。

# 例

```julia-repl
julia> get_valid_symbols("AAPL","AMD","asdfs")
2-element Vector{String}:
 "AAPL"
 "AMD"
```
