```
get_dividends(symbol::String; startdt::Union{Date,DateTime,AbstractString}="", enddt::Union{Date,DateTime,AbstractString}="", timeout::Int=10, throw_error::Bool=false, exchange_local_time::Bool=false)
```

Retrieves dividend data from Yahoo Finance.

## Arguments

  * `symbol`: A ticker (e.g., AAPL for Apple Inc., or ^GSPC for the S&P 500)
  * `startdt` and `enddt`: Optional. Can be of type `Date`, `DateTime`, or a `String` in the format "yyyy-mm-dd". If not provided, `startdt` defaults to the earliest available data and `enddt` to the current date.
  * `timeout`: Integer, defaults to 10. The timeout for the HTTP request in seconds.
  * `throw_error`: Boolean, defaults to `false`. If set to true, the function raises an error when the ticker is not valid or other issues occur. If false, a warning is given and an empty `OrderedDict` is returned.
  * `exchange_local_time`: Boolean, defaults to `false`. If set to true, the timestamp corresponds to the exchange local time; otherwise, it's in GMT.

## Returns

An `OrderedDict{String, Union{String,Vector{DateTime},Vector{Float64}}}` containing the following keys:

  * ticker
  * timestamp
  * div

# Examples

```julia
julia> get_dividends("AAPL", startdt = "2021-01-01", enddt="2022-01-01")
OrderedDict{String, Union{String,Vector{DateTime},Vector{Float64}}} with 3 entries:
  "ticker"    => "AAPL"
  "timestamp" => [DateTime("2021-02-05T14:30:00"), DateTime("2021-05-07T13:30:00"), DateTime("2021-08-06T13:30:00"), DateTime("2021-11-05T13:30:00")]
  "div"       => [0.205, 0.22, 0.22, 0.22]

## Can be easily converted to a DataFrame
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

## Broadcasting
julia> get_dividends.(["AAPL", "F"], startdt = "2021-01-01", enddt="2022-01-01")
2-element Vector{OrderedDict{String, Union{String,Vector{DateTime},Vector{Float64}}}}:
 OrderedDict("ticker" => "AAPL", "timestamp" => [DateTime("2021-02-05T14:30:00"), DateTime("2021-05-07T13:30:00"), DateTime("2021-08-06T13:30:00"), DateTime("2021-11-05T13:30:00")], "div" => [0.205, 0.22, 0.22, 0.22])
 OrderedDict("ticker" => "F", "timestamp" => [DateTime("2021-11-18T14:30:00")], "div" => [0.1])

## Converting it to a DataFrame:
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
