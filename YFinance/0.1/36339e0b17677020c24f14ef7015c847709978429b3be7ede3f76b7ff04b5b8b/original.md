```
get_prices(symbol::String; range::String="5d", interval::String="1d", startdt::Union{Date,DateTime,AbstractString}="", enddt::Union{Date,DateTime,AbstractString}="", prepost::Bool=false, autoadjust::Bool=true, timeout::Int=10, throw_error::Bool=false, exchange_local_time::Bool=false, divsplits::Bool=false, wait::Float64=0.0)
```

Retrieves prices from Yahoo Finance.

## Arguments

  * `symbol`: A ticker (e.g., AAPL for Apple Inc., or ^GSPC for the S&P 500)

You can either provide a `range` or both `startdt` and `enddt`.

  * `range`: A string specifying the time range. It can be one of the predefined values ("ytd", "max") or a custom range using the following suffixes:

      * "m" for minutes (e.g., "30m" for 30 minutes)
      * "d" for days (e.g., "7d" for 7 days)
      * "mo" for months (e.g., "3mo" for 3 months)
      * "y" for years (e.g., "1y" for 1 year)
  * `startdt` and `enddt`: Can be of type `Date`, `DateTime`, or a `String` in the format "yyyy-mm-dd". Both must be provided if one is specified.
  * `interval`: The data interval. Valid values are "1m", "2m", "5m", "15m", "30m", "60m", "90m", "1h", "1d", "5d", "1wk", "1mo", "3mo". Defaults to "1d".
  * `prepost`: Boolean indicating whether pre and post market data should be included. Defaults to `false`.
  * `autoadjust`: Defaults to `true`. Adjusts open, high, low, close prices, and volume by multiplying by the ratio between the close and the adjusted close prices - only available for intervals of 1d and up.
  * `timeout`: The timeout for the HTTP request in seconds. Defaults to 10.
  * `throw_error`: Boolean, defaults to `false`. If set to true, the function raises an error when the ticker is not valid or other issues occur. If false, a warning is given and an empty `OrderedDict` is returned.
  * `exchange_local_time`: Boolean, defaults to `false`. If set to true, the timestamp corresponds to the exchange local time; otherwise, it's in GMT.
  * `divsplits`: Boolean, defaults to `false`. If set to true, dividends and stock split data are also returned. Split data contains the numerator, denominator, and split ratio. The interval needs to be set to "1d" for this to work.
  * `wait`: Float, defaults to 0.0. Specifies the wait time in seconds between consecutive API calls when fetching minute data over extended periods.

## Notes

  * For minute data requests over periods longer than 7 days, the function automatically splits the request into multiple 7-day chunks and combines the results.
  * When using `startdt` and `enddt`, both must be provided.

## Returns

An `OrderedDict{String, Union{String,Vector{DateTime},Vector{Float64}}}` containing the requested data.

## Examples

```julia
julia> get_prices("AAPL", range="1d", interval="90m")
OrderedDict{String, Union{String,Vector{DateTime},Vector{Float64}}} with 7 entries:
  "ticker"    => "AAPL"
  "timestamp" => [DateTime("2022-12-29T14:30:00"), DateTime("2022-12-29T16:00:00"), DateTime("2022-12-29T17:30:00"), DateTime("2022-12-29T19:00:00"), DateTime("2022-12-29T20:30:00"), DateTime("2022-12-29T21:00:00")]   
  "open"      => [127.99, 129.96, 129.992, 130.035, 129.95, 129.61]
  "high"      => [129.98, 130.481, 130.098, 130.24, 130.22, 129.61]
  "low"       => [127.73, 129.44, 129.325, 129.7, 129.56, 129.61]
  "close"     => [129.954, 129.998, 130.035, 129.95, 129.6, 129.61]
  "vol"       => [2.9101646e7, 1.4058713e7, 9.897737e6, 9.552323e6, 6.308537e6, 0.0]

## Can be easily converted to a DataFrame
julia> using DataFrames
julia> get_prices("AAPL", range="1d", interval="90m") |> DataFrame
6×7 DataFrame
 Row │ ticker  timestamp            open     high     low      close    vol       
     │ String  DateTime             Float64  Float64  Float64  Float64  Float64   
─────┼────────────────────────────────────────────────────────────────────────────
   1 │ AAPL    2022-12-29T14:30:00  127.99   129.98   127.73   129.954  2.9101646e7
   2 │ AAPL    2022-12-29T16:00:00  129.96   130.481  129.44   129.998  1.4058713e7
   3 │ AAPL    2022-12-29T17:30:00  129.992  130.098  129.325  130.035  9.897737e6
   4 │ AAPL    2022-12-29T19:00:00  130.035  130.24   129.7    129.95   9.552323e6
   5 │ AAPL    2022-12-29T20:30:00  129.95   130.22   129.56   129.6    6.308537e6
   6 │ AAPL    2022-12-29T21:00:00  129.61   129.61   129.61   129.61   0.0

## Broadcasting
julia> get_prices.(["AAPL","NFLX"], range="1d", interval="90m")
2-element Vector{OrderedDict{String, Union{String, Vector{DateTime}, Vector{Float64}}}}:
 OrderedDict{String, Union{String, Vector{DateTime}, Vector{Float64}}} with 7 entries:
  "ticker"    => "AAPL"
  "timestamp" => [DateTime("2022-12-29T14:30:00"), DateTime("2022-12-29T16:00:00"), DateTime("2022-12-29T17:30:00"), DateTime("2022-12-29T19:00:00"), DateTime("2022-12-29T20:30:00"), DateTime("2022-12-29T21:00:00")]
  "open"      => [127.98999786376953, 129.9600067138672, 129.99240112304688, 130.03500366210938, 129.9499969482422, 129.61000061035156]
  "high"      => [129.97999572753906, 130.4813995361328, 130.09829711914062, 130.24000549316406, 130.22000122070312, 129.61000061035156]
  "low"       => [127.7300033569336, 129.44000244140625, 129.3249969482422, 129.6999969482422, 129.55999755859375, 129.61000061035156]
  "close"     => [129.95419311523438, 129.99830627441406, 130.03500366210938, 129.9499969482422, 129.60000610351562, 129.61000061035156]
  "vol"       => [2.9101646e7, 1.4058713e7, 9.897737e6, 9.552323e6, 6.308537e6, 0.0]
 OrderedDict{String, Union{String, Vector{DateTime}, Vector{Float64}}} with 7 entries:
  "ticker"    => "NFLX"
  "timestamp" => [DateTime("2022-12-29T14:30:00"), DateTime("2022-12-29T16:00:00"), DateTime("2022-12-29T17:30:00"), DateTime("2022-12-29T19:00:00"), DateTime("2022-12-29T20:30:00"), DateTime("2022-12-29T21:00:00")]
  "open"      => [283.17999267578125, 289.5199890136719, 293.4200134277344, 290.05499267578125, 290.760009765625, 291.1199951171875]
  "high"      => [291.8699951171875, 295.4999084472656, 293.5, 291.32000732421875, 292.3299865722656, 291.1199951171875]
  "low"       => [281.010009765625, 289.489990234375, 289.5400085449219, 288.7699890136719, 290.5400085449219, 291.1199951171875]
  "close"     => [289.5199890136719, 293.46990966796875, 290.04998779296875, 290.82000732421875, 291.1199951171875, 291.1199951171875]
  "vol"       => [2.950791e6, 2.458057e6, 1.362915e6, 1.212217e6, 1.121821e6, 0.0]

## Converting it to a DataFrame:
julia> using DataFrames
julia> data = get_prices.(["AAPL","NFLX"], range="1d", interval="90m");
julia> vcat([DataFrame(i) for i in data]...)
12×7 DataFrame
 Row │ ticker  timestamp            open     high     low      close    vol       
     │ String  DateTime             Float64  Float64  Float64  Float64  Float64   
─────┼────────────────────────────────────────────────────────────────────────────
   1 │ AAPL    2022-12-29T14:30:00  127.99   129.98   127.73   129.954  2.9101646e7
   2 │ AAPL    2022-12-29T16:00:00  129.96   130.481  129.44   129.998  1.4058713e7
   3 │ AAPL    2022-12-29T17:30:00  129.992  130.098  129.325  130.035  9.897737e6
   4 │ AAPL    2022-12-29T19:00:00  130.035  130.24   129.7    129.95   9.552323e6
   5 │ AAPL    2022-12-29T20:30:00  129.95   130.22   129.56   129.6    6.308537e6
   6 │ AAPL    2022-12-29T21:00:00  129.61   129.61   129.61   129.61   0.0
   7 │ NFLX    2022-12-29T14:30:00  283.18   291.87   281.01   289.52   2.950791e6
   8 │ NFLX    2022-12-29T16:00:00  289.52   295.5    289.49   293.47   2.458057e6
   9 │ NFLX    2022-12-29T17:30:00  293.42   293.5    289.54   290.05   1.362915e6
  10 │ NFLX    2022-12-29T19:00:00  290.055  291.32   288.77   290.82   1.212217e6
  11 │ NFLX    2022-12-29T20:30:00  290.76   292.33   290.54   291.12   1.121821e6
  12 │ NFLX    2022-12-29T21:00:00  291.12   291.12   291.12   291.12   0.0
```
