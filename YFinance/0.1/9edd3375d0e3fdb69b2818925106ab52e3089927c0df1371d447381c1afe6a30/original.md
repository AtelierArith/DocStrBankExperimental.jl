```
get_quoteSummary(symbol::String; item=nothing)
```

Retrievs general information from Yahoo Finance stored in a JSON3 object.

## Arguments

  * smybol`::String` is a ticker (e.g. AAPL for Apple Computers, or ^GSPC for the S&P500)
  * item can either be a string or multiple items as a `Vector` of `Strings`. To see valid items call `_QuoteSummary_Items` (not all items are available for all types of securities)
  * throw_error`::Bool` defaults to `false`. If set to true the function errors when the ticker is not valid. Else a warning is given and an empty `JSON3.Object` is returned.

# Examples

```julia-repl
julia> get_quoteSummary("AAPL")

JSON3.Object{Vector{UInt8}, SubArray{UInt64, 1, Vector{UInt64}, Tuple{UnitRange{Int64}}, true}} with 31 entries:
:assetProfile             => {…
:recommendationTrend      => {…
:cashflowStatementHistory => {…

⋮                         => ⋮
julia> get_quoteSummary("AAPL",item = "quoteType")
JSON3.Object{Vector{UInt8}, SubArray{UInt64, 1, Vector{UInt64}, Tuple{UnitRange{Int64}}, true}} with 13 entries:
:exchange               => "NMS"
:quoteType              => "EQUITY"
:symbol                 => "AAPL"
⋮                       => ⋮
```
