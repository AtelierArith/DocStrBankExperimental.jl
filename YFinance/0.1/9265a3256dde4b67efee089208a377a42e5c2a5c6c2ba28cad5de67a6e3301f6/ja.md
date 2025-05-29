```
get_summary_detail(quoteSummary::JSON3.Object)
```

quote summaryからsummaryDetailアイテムを取得します。

## 引数

`get_quoteSummary(symbol::String; item=nothing,throw_error=false)`から返された`JSON3.Object`または`AbstractString`型のティッカーシンボルのいずれかです。ティッカーシンボルが提供された場合、最初に`get_quoteSummary(symbol::String)`が呼び出されます。

# 例

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
