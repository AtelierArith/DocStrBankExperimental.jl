```
dediac(s::String)
```

入力の `String` オブジェクトからダイアクリティカルマークを削除します。

# 例

```julia-repl
julia> bw_basmala = "bisomi {ll~ahi {lr~aHoma`ni {lr~aHiymi"
julia> dediac(bw_basmala)
"bsm {llh {lrHmn {lrHym"
julia> dediac(arabic(bw_basmala))
"بسم ٱلله ٱلرحمن ٱلرحيم"
```
