```
get_splits(symbol::String; startdt::Union{Date,DateTime,AbstractString}="", enddt::Union{Date,DateTime,AbstractString}="", timeout::Int=10, throw_error::Bool=false, exchange_local_time::Bool=false)
```

Yahoo Financeから株式分割データを取得します。

## 引数

  * `symbol`: ティッカー（例：Apple Inc.のAAPL、またはS&P 500の^GSPC）
  * `startdt`および`enddt`: オプション。`Date`、`DateTime`、または"yyyy-mm-dd"形式の`String`のいずれかの型を取ることができます。指定しない場合、`startdt`は利用可能な最も早いデータにデフォルト設定され、`enddt`は現在の日付に設定されます。
  * `timeout`: 整数、デフォルトは10。HTTPリクエストのタイムアウト（秒単位）。
  * `throw_error`: ブール値、デフォルトは`false`。trueに設定すると、ティッカーが無効であるか、他の問題が発生した場合にエラーを発生させます。falseの場合は警告が表示され、空の`OrderedDict`が返されます。
  * `exchange_local_time`: ブール値、デフォルトは`false`。trueに設定すると、タイムスタンプは取引所の現地時間に対応し、そうでない場合はGMTになります。

## 戻り値

要求された分割データを含む`OrderedDict{String, Union{String,Vector{DateTime},Vector{Int},Vector{Float64}}}`。

# 例

```julia
julia> get_splits("AAPL", startdt = "2000-01-01", enddt = "2020-01-01")
OrderedDict{String, Union{String,Vector{DateTime},Vector{Int},Vector{Float64}}} with 5 entries:
  "ticker"      => "AAPL"
  "timestamp"   => [DateTime("2000-06-21T13:30:00"), DateTime("2005-02-28T14:30:00"), DateTime("2014-06-09T13:30:00")]
  "numerator"   => [2, 2, 7]
  "denominator" => [1, 1, 1]
  "ratio"       => [2.0, 2.0, 7.0]

## DataFrameに簡単に変換可能
julia> using DataFrames
julia> get_splits("AAPL", startdt = "2000-01-01", enddt = "2020-01-01") |> DataFrame
3×5 DataFrame
 Row │ ticker  timestamp            numerator  denominator  ratio   
     │ String  DateTime             Int64      Int64        Float64 
─────┼──────────────────────────────────────────────────────────────
   1 │ AAPL    2000-06-21T13:30:00          2            1      2.0
   2 │ AAPL    2005-02-28T14:30:00          2            1      2.0
   3 │ AAPL    2014-06-09T13:30:00          7            1      7.0

## ブロードキャスティング
julia> get_splits.(["AAPL", "F"], startdt = "2000-01-01", enddt = "2020-01-01")
2-element Vector{OrderedDict{String, Union{String,Vector{DateTime},Vector{Int},Vector{Float64}}}}:
 OrderedDict("ticker" => "AAPL", "timestamp" => [DateTime("2000-06-21T13:30:00"), DateTime("2005-02-28T14:30:00"), DateTime("2014-06-09T13:30:00")], "numerator" => [2, 2, 7], "denominator" => [1, 1, 1], "ratio" => [2.0, 2.0, 7.0])
 OrderedDict("ticker" => "F", "timestamp" => [DateTime("2000-06-29T13:30:00"), DateTime("2000-08-03T13:30:00")], "numerator" => [10000, 1748175], "denominator" => [9607, 1000000], "ratio" => [1.0409076714895389, 1.748175])

## DataFrameへの変換：
julia> using DataFrames
julia> data = get_splits.(["AAPL", "F"], startdt = "2000-01-01", enddt = "2020-01-01");

julia> vcat([DataFrame(i) for i in data]...)
5×5 DataFrame
 Row │ ticker  timestamp            numerator  denominator  ratio   
     │ String  DateTime             Int64      Int64        Float64 
─────┼──────────────────────────────────────────────────────────────
   1 │ AAPL    2000-06-21T13:30:00          2            1  2.0
   2 │ AAPL    2005-02-28T14:30:00          2            1  2.0
   3 │ AAPL    2014-06-09T13:30:00          7            1  7.0
   4 │ F       2000-06-29T13:30:00      10000         9607  1.04091
   5 │ F       2000-08-03T13:30:00    1748175      1000000  1.74818
```
