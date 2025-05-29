```
get_summary_detail(quoteSummary::JSON3.Object)
```

Retrievs the summaryDetail Item from the quote summary.

## Arguments

Can be either a `JSON3.Object` returned from `get_quoteSummary(symbol::String; item=nothing,throw_error=false)` or a ticker symbol of type `AbstractString` If a ticker symbol is provided `get_quoteSummary(symbol::String)` is called first. 

# Examples

```julia-repl
julia> get_quoteSummary("AAPL") |> get_summary_detail
OrderedDict{String, Any} with 41 entries:
  "priceHint"                  => 2
  "previousClose"              => 126.04
  "open"                       => 127.99
  "dayLow"                     => 127.815
  "dayHigh"                    => 130.48
  "regularMarketPreviousClose" => 126.04
  "regularMarketOpen"          => 127.99
  "regularMarketDayLow"        => 127.815
  "regularMarketDayHigh"       => 130.48
  "dividendRate"               => 0.92
  "dividendYield"              => 0.0073
  "exDividendDate"             => 1667520000
  "payoutRatio"                => 0.1473
  "fiveYearAvgDividendYield"   => 0.99
  "beta"                       => 1.21947
  "trailingPE"                 => 21.2128
  "forwardPE"                  => 19.1448
  ⋮                            => ⋮

julia> get_summary_detail("AAPL")
OrderedDict{String, Any} with 41 entries:
  "priceHint"                  => 2
  "previousClose"              => 126.04
  "open"                       => 127.99
  "dayLow"                     => 127.815
  "dayHigh"                    => 130.48
  "regularMarketPreviousClose" => 126.04
  "regularMarketOpen"          => 127.99
  "regularMarketDayLow"        => 127.815
  "regularMarketDayHigh"       => 130.48
  "dividendRate"               => 0.92
  "dividendYield"              => 0.0073
  "exDividendDate"             => 1667520000
  "payoutRatio"                => 0.1473
  "fiveYearAvgDividendYield"   => 0.99
  "beta"                       => 1.21947
  "trailingPE"                 => 21.2128
  "forwardPE"                  => 19.1448
  ⋮                            => ⋮
```
