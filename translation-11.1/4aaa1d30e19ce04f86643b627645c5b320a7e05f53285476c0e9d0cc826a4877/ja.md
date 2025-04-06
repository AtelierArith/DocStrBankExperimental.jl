```
Time(t::AbstractString, df::DateFormat=ISOTimeFormat) -> Time
```

`t` 日付時刻文字列を [`DateFormat`](@ref) オブジェクトで指定されたパターンに従って解析することによって `Time` を構築します。省略した場合は、dateformat"HH:MM:SS.s" が使用されます。

`Time(::AbstractString, ::AbstractString)` と似ていますが、事前に作成された `DateFormat` オブジェクトを使用して、同様の形式の時刻文字列を繰り返し解析する際により効率的です。
