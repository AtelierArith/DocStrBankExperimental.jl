```
titles(x::YahooNews)
```

Returns the titles of all `NewsItem`s in a `Vector`

# Arugments:

  * x`::YahooNews`

# Returns:

  * `Vector{String}`

# Example:

```julia
julia> x = search_news("MSFT");

julia> titles(x)
8-element Vector{String}:
 "Microsoft Removes Twitter From Ad Program; Musk Threatens Suit"
 "AI ChatBots Guzzle Water. How and Why It s a Problem."
 "Best Dow Jones Stocks To Buy And Watch In April: Travelers Surges On Earnings"
 "Top Companies for Financial Strength"
 "VIDEO: Your Top Questions Answe" ⋯ 17 bytes ⋯ "eiling and Portfolio Management"
 "Microsoft agrees to buy 50m Foxconn parcel in Wisconsin"
 "LinkedIn Reveals Top Workplace:" ⋯ 19 bytes ⋯ "etflix Rank For Happy Employees"
 "Microsoft Working With Space an" ⋯ 24 bytes ⋯ "Blockchain Data for Azure Cloud"
```
