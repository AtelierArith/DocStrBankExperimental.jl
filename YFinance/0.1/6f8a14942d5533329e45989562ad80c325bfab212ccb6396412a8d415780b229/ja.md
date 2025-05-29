```
get_all_symbols(market::T)::Vector{T} where {T<:String}
```

指定された `market` からすべてのシンボルを取得します。

# 引数

  * `market::String`: シンボルを取得する市場。

現在サポートされている市場は次のとおりです：

  * `AMEX`
  * `NASDAQ`
  * `NYSE`

dumbstockapi.comを使用します。

# 戻り値

  * `Vector{String}`: シンボルを含む文字列のベクター。

# 例

```julia
julia> get_all_symbols("NYSE")
3127-element Vector{String}:
 "A"
 "AA"
 "AAC"
 "AAN"
 ⋮
 "ZTR"
 "ZTS"
 "ZUO"
 "ZYME"
```
