```
timestamps(x::YahooNews)
```

すべての `NewsItem` のタイムスタンプを `Vector` で返します

# 引数:

  * x`::YahooNews`

# 返り値:

  * `Vector{DateTime}`

# 例:

```julia
julia> x = search_news("MSFT");

julia> timestamps(x)
8-element Vector{Dates.DateTime}:
 2023-04-19T22:11:21
 2023-04-19T20:33:00
 2023-04-19T18:06:33
 2023-04-19T18:03:00
 2023-04-19T16:46:00
 2023-04-19T16:36:30
 2023-04-19T15:54:27
 2023-04-19T15:00:00
```
