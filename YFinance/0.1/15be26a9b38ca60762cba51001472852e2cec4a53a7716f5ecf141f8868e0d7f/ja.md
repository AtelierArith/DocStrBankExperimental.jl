```
get_calendar_events(quoteSummary::JSON3.Object)
```

引用の要約からカレンダーイベントを取得します。

## 引数

`get_quoteSummary(symbol::String; item=nothing,throw_error=false)` から返された `JSON3.Object` か、`AbstractString` 型のティッカーシンボルのいずれかです。ティッカーシンボルが提供されると、最初に `get_quoteSummary(symbol::String)` が呼び出されます。

# 例

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
