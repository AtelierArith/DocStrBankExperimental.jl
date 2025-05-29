```
get_sector_industry(quoteSummary::JSON3.Object)
```

引用要約からセクターと業界を取得します。

## 引数

`get_quoteSummary(symbol::String; item=nothing,throw_error=false)`から返された`JSON3.Object`であるか、`AbstractString`型のティッカーシンボルである必要があります。ティッカーシンボルが提供された場合、最初に`get_quoteSummary(symbol::String)`が呼び出されます。

# 例

```julia-repl
julia> get_quoteSummary("AAPL") |> get_sector_industry
OrderedDict{String, String} with 2 entries:
  "sector"   => "Technology"
  "industry" => "Consumer Electronics"

julia> get_sector_industry("AAPL")
OrderedDict{String, String} with 2 entries:
  "sector"   => "Technology"
  "industry" => "Consumer Electronics"
```
