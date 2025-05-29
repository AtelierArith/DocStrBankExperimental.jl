```
search_news(str::String;lang="en-us")
```

Returns news related to the seach string `str`.

# Arugments:

  * str`::String`: The search string. It is usually a symbol.
  * lang`::String`: The search language and region. The region is automatically set according to the language. Supported languages are: "en-us", "en-ca", "en-gb", "en-au", "en-nz", "en-SG", "en-in", "de", "es", "fr", "it", "pt-br", "zh", and "zh-tw".

# Returns:

  * `YahooNews <: AbstractArray` that contains  `NewsItem`s with fields: title`::String`, publisher`::String`, link`::String`, timestamp`::DateTime`, symbols`::Array{String,1}`

# Example:

```julia
julia> search_news("MSFT")
8-element YahooNews{NewsItem, 1}:
 Title:          Microsoft Removes Twitter From Ad Program; Musk Threatens Suit
Timestamp:       Apr 19 22:11 PM
Publisher:       Bloomberg
Link:            https://finance.yahoo.com/news/microsoft-removes-twitter-ad-program-221121298.html
Symbols:         MSFT

 Title:          AI ChatBots Guzzle Water. How and Why It’s a Problem.
Timestamp:       Apr 19 20:33 PM
Publisher:       Barrons.com
Link:            https://finance.yahoo.com/m/06a973de-215d-3928-9c99-00867b512966/ai-chatbots-guzzle-water.-how.html
Symbols:         GOOGL, MSFT

 Title:          Best Dow Jones Stocks To Buy And Watch In April: Travelers Surges On Earnings
Timestamp:       Apr 19 18:06 PM
Publisher:       Investor's Business Daily
Link:            https://finance.yahoo.com/m/65b53896-faf4-3a06-9d0d-a63cf3c83192/best-dow-jones-stocks-to-buy.html
Symbols:         ^DJI, MSFT

 Title:          Top Companies for Financial Strength
Timestamp:       Apr 19 18:03 PM
Publisher:       The Wall Street Journal
Link:            https://finance.yahoo.com/m/9c4f6782-7ce7-3e1e-8d0a-ff7f41bc5ef7/top-companies-for-financial.html
Symbols:         XOM, MSFT, AAPL, NUE, MRNA

 Title:          VIDEO: Your Top Questions Answered on the Debt Ceiling and Portfolio Management
Timestamp:       Apr 19 16:46 PM
Publisher:       TheStreet.com
Link:            https://finance.yahoo.com/m/ebf41ba6-6cbc-38ce-93c5-bcee152080e7/video%3A-your-top-questions.html
Symbols:         CHPT, MSFT

 Title:          Microsoft agrees to buy 50m Foxconn parcel in Wisconsin
Timestamp:       Apr 19 16:36 PM
Publisher:       AP Finance
Link:            https://finance.yahoo.com/news/board-oks-microsoft-data-center-163630944.html
Symbols:         MSFT

 Title:          LinkedIn Reveals Top Workplace: Where Amazon and Netflix Rank For Happy Employees
Timestamp:       Apr 19 15:54 PM
Publisher:       Benzinga
Link:            https://finance.yahoo.com/news/linkedin-reveals-top-workplace-where-155427039.html
Symbols:         AMZN, GOOGL, MSFT, NFLX, WFC

 Title:          Microsoft Working With Space and Time to Add Real-Time Blockchain Data for Azure Cloud
Timestamp:       Apr 19 15:00 PM
Publisher:       CoinDesk
Link:            https://finance.yahoo.com/news/microsoft-working-space-time-add-150000132.html
Symbols:         MSFT
```
