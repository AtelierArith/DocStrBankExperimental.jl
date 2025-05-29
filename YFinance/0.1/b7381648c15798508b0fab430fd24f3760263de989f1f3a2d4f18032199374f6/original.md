```
get_valid_symbols(symbol::AbstractVector{<:AbstractString})
```

Takes a `AbstractVector` of symbols and returns only the valid ones.

# Arguments

  * smybol`::AbstractVector{<:AbstractString}` is a vector of tickers (e.g. AAPL for Apple Computers, or ^GSPC for the S&P500)

# Examples

```julia-repl
julia> get_valid_symbols("AAPL","AMD","asdfs")
2-element Vector{String}:
 "AAPL"
 "AMD"
```
