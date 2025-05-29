```
get_calendar_events(quoteSummary::JSON3.Object)
```

Retrievs calendar events from the quote summary.

## Arguments

Can be either a `JSON3.Object` returned from `get_quoteSummary(symbol::String; item=nothing,throw_error=false)` or a ticker symbol of type `AbstractString` If a ticker symbol is provided `get_quoteSummary(symbol::String)` is called first. 

# Examples

```julia-repl
julia> get_quoteSummary("AAPL") |> get_calendar_events
OrderedDict{String, Any} with 3 entries:
  "dividend_date"   => DateTime("2022-11-10T00:00:00")
  "earnings_dates"  => [DateTime("2023-01-25T10:59:00"), DateTime("2023-01-30T12:00:00")]
  "exdividend_date" => DateTime("2022-11-04T00:00:00")

julia> get_calendar_events("AAPL")
OrderedDict{String, Any} with 3 entries:
  "dividend_date"   => DateTime("2022-11-10T00:00:00")
  "earnings_dates"  => [DateTime("2023-01-25T10:59:00"), DateTime("2023-01-30T12:00:00")]
  "exdividend_date" => DateTime("2022-11-04T00:00:00")

julia> using DataFrames
julia> get_calendar_events("AAPL") |> DataFrame
2×3 DataFrame
 Row │ dividend_date        earnings_dates       exdividend_date     
     │ DateTime             DateTime             DateTime
─────┼───────────────────────────────────────────────────────────────
   1 │ 2022-11-10T00:00:00  2023-01-25T10:59:00  2022-11-04T00:00:00
   2 │ 2022-11-10T00:00:00  2023-01-30T12:00:00  2022-11-04T00:00:00
```
