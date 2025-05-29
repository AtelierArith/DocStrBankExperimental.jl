```
get_all_symbols(market::T)::Vector{T} where {T<:String}
```

Fetch all the symbols from a given `market`.

# Arguments

  * `market::String`: The market to fetch the symbols from.

Currently supported markets are:

  * `AMEX`
  * `NASDAQ`
  * `NYSE`

Uses dumbstockapi.com

# Returns

  * `Vector{String}`: A vector of strings containing the symbols.

# Example

```julia
julia> get_all_symbols("NYSE")
3127-element Vector{String}:
 "A"
 "AA"
 "AAC"
 "AAN"
 ⋮
 "ZTR"
 "ZTS"
 "ZUO"
 "ZYME"
```
