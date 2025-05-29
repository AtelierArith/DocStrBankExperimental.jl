```
get_dividends(symbol::String; startdt::Union{Date,DateTime,AbstractString}="", enddt::Union{Date,DateTime,AbstractString}="", timeout::Int=10, throw_error::Bool=false, exchange_local_time::Bool=false)
```

Yahoo Financeから配当データを取得します。

## 引数

  * `symbol`: ティッカー（例：Apple Inc.のAAPL、またはS&P 500の^GSPC）
  * `startdt`と`enddt`: オプション。`Date`、`DateTime`、または"yyyy-mm-dd"形式の`String`のいずれかの型を取ることができます。指定しない場合、`startdt`は利用可能な最も早いデータにデフォルト設定され、`enddt`は現在の日付に設定されます。
  * `timeout`: 整数、デフォルトは10。HTTPリクエストのタイムアウト（秒）。
  * `throw_error`: ブール値、デフォルトは`false`。trueに設定すると、ティッカーが無効であるか、他の問題が発生した場合にエラーを発生させます。falseの場合は警告が表示され、空の`OrderedDict`が返されます。
  * `exchange_local_time`: ブール値、デフォルトは`false`。trueに設定すると、タイムスタンプは取引所の現地時間に対応し、そうでない場合はGMTになります。

## 戻り値

以下のキーを含む`OrderedDict{String, Union{String,Vector{DateTime},Vector{Float64}}}`を返します：

  * ticker
  * timestamp
  * div

# 例

```julia
julia> get_dividends("AAPL", startdt = "2021-01-01", enddt="2022-01-01")
OrderedDict{String, Union{String,Vector{DateTime},Vector{Float64}}} with 3 entries:
  "ticker"    => "AAPL"
  "timestamp" => [DateTime("2021-02-05T14:30:00"), DateTime("2021-05-07T13:30:00"), DateTime("2021-08-06T13:30:00"), DateTime("2021-11-05T13:30:00")]
  "div"       => [0.205, 0.22, 0.22, 0.22]

## DataFrameに簡単に変換可能
julia> using DataFrames
julia> get_dividends("AAPL", startdt = "2021-01-01", enddt="2022-01-01") |> DataFrame
4×3 DataFrame
 Row │ ticker  timestamp            div     
     │ String  DateTime             Float64 
─────┼───────────────────────────────────────
   1 │ AAPL    2021-02-05T14:30:00    0.205
   2 │ AAPL    2021-05-07T13:30:00    0.22
   3 │ AAPL    2021-08-06T13:30:00    0.22
   4 │ AAPL    2021-11-05T13:30:00    0.22

## ブロードキャスティング
julia> get_dividends.(["AAPL", "F"], startdt = "2021-01-01", enddt="2022-01-01")
2-element Vector{OrderedDict{String, Union{String,Vector{DateTime},Vector{Float64}}}}:
 OrderedDict("ticker" => "AAPL", "timestamp" => [DateTime("2021-02-05T14:30:00"), DateTime("2021-05-07T13:30:00"), DateTime("2021-08-06T13:30:00"), DateTime("2021-11-05T13:30:00")], "div" => [0.205, 0.22, 0.22, 0.22])
 OrderedDict("ticker" => "F", "timestamp" => [DateTime("2021-11-18T14:30:00")], "div" => [0.1])

## DataFrameへの変換：
julia> using DataFrames
julia> data = get_dividends.(["AAPL", "F"], startdt = "2021-01-01", enddt="2022-01-01");

julia> vcat([DataFrame(i) for i in data]...)
5×3 DataFrame
 Row │ ticker  timestamp            div     
     │ String  DateTime             Float64 
─────┼───────────────────────────────────────
   1 │ AAPL    2021-02-05T14:30:00    0.205
   2 │ AAPL    2021-05-07T13:30:00    0.22
   3 │ AAPL    2021-08-06T13:30:00    0.22
   4 │ AAPL    2021-11-05T13:30:00    0.22
   5 │ F       2021-11-18T14:30:00    0.1
```
