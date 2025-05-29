```
get_splits(symbol::String; startdt::Union{Date,DateTime,AbstractString}="", enddt::Union{Date,DateTime,AbstractString}="", timeout::Int=10, throw_error::Bool=false, exchange_local_time::Bool=false)
```

Retrieves stock split data from Yahoo Finance.

## Arguments

  * `symbol`: A ticker (e.g., AAPL for Apple Inc., or ^GSPC for the S&P 500)
  * `startdt` and `enddt`: Optional. Can be of type `Date`, `DateTime`, or a `String` in the format "yyyy-mm-dd". If not provided, `startdt` defaults to the earliest available data and `enddt` to the current date.
  * `timeout`: Integer, defaults to 10. The timeout for the HTTP request in seconds.
  * `throw_error`: Boolean, defaults to `false`. If set to true, the function raises an error when the ticker is not valid or other issues occur. If false, a warning is given and an empty `OrderedDict` is returned.
  * `exchange_local_time`: Boolean, defaults to `false`. If set to true, the timestamp corresponds to the exchange local time; otherwise, it's in GMT.

## Returns

An `OrderedDict{String, Union{String,Vector{DateTime},Vector{Int},Vector{Float64}}}` containing the requested split data.

# Examples

```julia
julia> get_splits("AAPL", startdt = "2000-01-01", enddt = "2020-01-01")
OrderedDict{String, Union{String,Vector{DateTime},Vector{Int},Vector{Float64}}} with 5 entries:
  "ticker"      => "AAPL"
  "timestamp"   => [DateTime("2000-06-21T13:30:00"), DateTime("2005-02-28T14:30:00"), DateTime("2014-06-09T13:30:00")]
  "numerator"   => [2, 2, 7]
  "denominator" => [1, 1, 1]
  "ratio"       => [2.0, 2.0, 7.0]

## Can be easily converted to a DataFrame
julia> using DataFrames
julia> get_splits("AAPL", startdt = "2000-01-01", enddt = "2020-01-01") |> DataFrame
3×5 DataFrame
 Row │ ticker  timestamp            numerator  denominator  ratio   
     │ String  DateTime             Int64      Int64        Float64 
─────┼──────────────────────────────────────────────────────────────
   1 │ AAPL    2000-06-21T13:30:00          2            1      2.0
   2 │ AAPL    2005-02-28T14:30:00          2            1      2.0
   3 │ AAPL    2014-06-09T13:30:00          7            1      7.0

## Broadcasting
julia> get_splits.(["AAPL", "F"], startdt = "2000-01-01", enddt = "2020-01-01")
2-element Vector{OrderedDict{String, Union{String,Vector{DateTime},Vector{Int},Vector{Float64}}}}:
 OrderedDict("ticker" => "AAPL", "timestamp" => [DateTime("2000-06-21T13:30:00"), DateTime("2005-02-28T14:30:00"), DateTime("2014-06-09T13:30:00")], "numerator" => [2, 2, 7], "denominator" => [1, 1, 1], "ratio" => [2.0, 2.0, 7.0])
 OrderedDict("ticker" => "F", "timestamp" => [DateTime("2000-06-29T13:30:00"), DateTime("2000-08-03T13:30:00")], "numerator" => [10000, 1748175], "denominator" => [9607, 1000000], "ratio" => [1.0409076714895389, 1.748175])

## Converting it to a DataFrame:
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
