```
links(x::YahooNews)
```

Returns the links of all `NewsItem`s in a `Vector`

# Arugments:

  * x`::YahooNews`

# Returns:

  * `Vector{String}`

# Example:

```julia
julia> x = search_news("MSFT");

julia> links(x)
8-element Vector{String}:
 "https://finance.yahoo.com/news/" ⋯ 20 bytes ⋯ "itter-ad-program-221121298.html"
 "https://finance.yahoo.com/m/06a" ⋯ 37 bytes ⋯ "chatbots-guzzle-water.-how.html"
 "https://finance.yahoo.com/m/65b" ⋯ 36 bytes ⋯ "st-dow-jones-stocks-to-buy.html"
 "https://finance.yahoo.com/m/9c4" ⋯ 35 bytes ⋯ "op-companies-for-financial.html"
 "https://finance.yahoo.com/m/ebf" ⋯ 35 bytes ⋯ "ideo%3A-your-top-questions.html"
 "https://finance.yahoo.com/news/board-oks-microsoft-data-center-163630944.html"
 "https://finance.yahoo.com/news/" ⋯ 20 bytes ⋯ "-workplace-where-155427039.html"
 "https://finance.yahoo.com/news/microsoft-working-space-time-add-150000132.html"
```
