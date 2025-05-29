```
get_upgrade_downgrade_history(quoteSummary::JSON3.Object)
```

引用概要からアップグレードおよびダウングレードの履歴を取得します。

## 引数

`get_quoteSummary(symbol::String; item=nothing,throw_error=false)`から返された`JSON3.Object`または`AbstractString`型のティッカーシンボルのいずれかである必要があります。ティッカーシンボルが提供された場合、最初に`get_quoteSummary(symbol::String)`が呼び出されます。

# 例

```julia-repl
julia> get_quoteSummary("AAPL") |> get_upgrade_downgrade_history
OrderedDict{String, Vector} with 5 entries:
  "firm"      => ["JP Morgan", "UBS", "Morgan Stanley", "B of A Securities", "Barclays", …  
  "date"      => Union{Missing, DateTime}[DateTime("2022-12-20T11:47:33"), DateTime("2022…  
  "toGrade"   => Union{Missing, String}["Overweight", "Buy", "Overweight", "Neutral", "Eq…  
  "fromGrade" => Union{Missing, String}["", "", "", "", "", "", "", "", "", ""  …  "", ""…  
  "action"    => Union{Missing, String}["main", "main", "main", "main", "main", "main", "…

julia> get_upgrade_downgrade_history("AAPL")
OrderedDict{String, Vector} with 5 entries:
  "firm"      => ["JP Morgan", "UBS", "Morgan Stanley", "B of A Securities", "Barclays", …  
  "date"      => Union{Missing, DateTime}[DateTime("2022-12-20T11:47:33"), DateTime("2022…  
  "toGrade"   => Union{Missing, String}["Overweight", "Buy", "Overweight", "Neutral", "Eq…  
  "fromGrade" => Union{Missing, String}["", "", "", "", "", "", "", "", "", ""  …  "", ""…  
  "action"    => Union{Missing, String}["main", "main", "main", "main", "main", "main", "…
  
julia> using DataFrames
julia> get_upgrade_downgrade_history("AAPL") |> DataFrame
872×5 DataFrame
 Row │ firm               date                 toGrade       fromGrade  action  
     │ String             DateTime?            String?       String?    String? 
─────┼──────────────────────────────────────────────────────────────────────────
   1 │ JP Morgan          2022-12-20T11:47:33  Overweight               main
   2 │ UBS                2022-11-08T12:17:03  Buy                      main
   3 │ Morgan Stanley     2022-11-08T12:14:23  Overweight               main
   4 │ B of A Securities  2022-11-07T13:08:30  Neutral                  main
   5 │ Barclays           2022-11-07T12:39:27  Equal-Weight             main
   6 │ Wedbush            2022-10-28T13:19:17  Outperform               main
   7 │ Credit Suisse      2022-10-28T11:59:30  Outperform               main
  ⋮  │         ⋮                   ⋮                ⋮            ⋮         ⋮
 867 │ Oxen Group         2012-03-14T15:25:00  Buy                      init
 868 │ Canaccord Genuity  2012-03-14T08:21:00  Buy                      main
 869 │ Morgan Stanley     2012-03-14T06:13:00  Overweight               main
 870 │ Jefferies          2012-03-13T06:08:00  Buy                      main
 871 │ FBN Securities     2012-03-08T07:33:00  Outperform               main
 872 │ Canaccord Genuity  2012-02-09T08:17:00  Buy                      main
                                                                859 rows omitted
```
