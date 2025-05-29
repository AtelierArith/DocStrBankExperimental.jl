```
get_earnings_estimates(quoteSummary::JSON3.Object)
```

Retrievs the earnings estimates from the quote summary.

## Arguments

Can be either a `JSON3.Object` returned from `get_quoteSummary(symbol::String; item=nothing,throw_error=false)` or a ticker symbol of type `AbstractString` If a ticker symbol is provided `get_quoteSummary(symbol::String)` is called first. 

# Examples

```julia-repl
julia> get_quoteSummary("AAPL") |> get_earnings_estimates
OrderedDict{String, Vector} with 3 entries:
  "quarter"  => ["4Q2021", "1Q2022", "2Q2022", "3Q2022", "4Q2022"]
  "estimate" => [1.89, 1.43, 1.16, 1.27, 1.98]
  "actual"   => Union{Missing, Float64}[2.1, 1.52, 1.2, 1.29, missing]

julia> get_earnings_estimates("AAPL")
OrderedDict{String, Vector} with 3 entries:
  "quarter"  => ["4Q2021", "1Q2022", "2Q2022", "3Q2022", "4Q2022"]
  "estimate" => [1.89, 1.43, 1.16, 1.27, 1.98]
  "actual"   => Union{Missing, Float64}[2.1, 1.52, 1.2, 1.29, missing]

julia> using DataFrames
julia> get_earnings_estimates("AAPL") |> DataFrame
5×3 DataFrame
 Row │ quarter  estimate  actual     
     │ String   Float64   Float64?   
─────┼───────────────────────────────
   1 │ 4Q2021       1.89        2.1
   2 │ 1Q2022       1.43        1.52
   3 │ 2Q2022       1.16        1.2
   4 │ 3Q2022       1.27        1.29
   5 │ 4Q2022       1.98  missing   
```
