```
get_major_holders_breakdown(quoteSummary::JSON3.Object)
```

Retrievs the breakdown of the major holders from the quote summary.

## Arguments

Can be either a `JSON3.Object` returned from `get_quoteSummary(symbol::String; item=nothing,throw_error=false)` or a ticker symbol of type `AbstractString` If a ticker symbol is provided `get_quoteSummary(symbol::String)` is called first. 

# Examples

```julia-repl
julia> get_quoteSummary("AAPL") |> get_major_holders_breakdown
OrderedDict{String, Real} with 4 entries:  
  "insidersPercentHeld"          => 0.00072
  "institutionsPercentHeld"      => 0.60915
  "institutionsFloatPercentHeld" => 0.60959
  "institutionsCount"            => 5526  

julia> get_major_holders_breakdown("AAPL")
OrderedDict{String, Real} with 4 entries:  
  "insidersPercentHeld"          => 0.00072
  "institutionsPercentHeld"      => 0.60915
  "institutionsFloatPercentHeld" => 0.60959
  "institutionsCount"            => 5526
```
