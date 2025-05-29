```
get_valid_symbols(symbol::AbstractString)
```

Takes a symbol. If the symbol is valid it returns the symbol in a vector if not it returns and empy vector.

# Arguments

  * smybol`::AbstractString` is a ticker (e.g. AAPL for Apple Computers, or ^GSPC for the S&P500)

# Examples

```julia-repl
julia> get_valid_symbols("AAPL")
1-element Vector{String}:
 "AAPL"

julia> get_valid_symbols("asdfs")
 String[]
```
