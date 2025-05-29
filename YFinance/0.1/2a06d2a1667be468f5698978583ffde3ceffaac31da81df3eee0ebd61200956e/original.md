```
get_sector_industry(quoteSummary::JSON3.Object)
```

Retrievs the Sector and Industry from the quote summary.

## Arguments

Can be either a `JSON3.Object` returned from `get_quoteSummary(symbol::String; item=nothing,throw_error=false)` or a ticker symbol of type `AbstractString` If a ticker symbol is provided `get_quoteSummary(symbol::String)` is called first. 

# Examples

```julia-repl
julia> get_quoteSummary("AAPL") |> get_sector_industry
OrderedDict{String, String} with 2 entries:
  "sector"   => "Technology"
  "industry" => "Consumer Electronics"

julia> get_sector_industry("AAPL")
OrderedDict{String, String} with 2 entries:
  "sector"   => "Technology"
  "industry" => "Consumer Electronics"
```
