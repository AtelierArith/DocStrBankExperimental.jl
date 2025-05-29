```
normalize(s::String, chars::Array{Symbol,1})
```

特定のアラビア語またはバクワルターの `String` 文字/s (`chars`) を正規化します。

# 例

```julia-repl
julia> ar_basmala = "بِسْمِ ٱللَّهِ ٱلرَّحْمَٰنِ ٱلرَّحِيمِ"
julia> normalize(ar_basmala, [:alif_khanjareeya, :hamzat_wasl]) === "بِسْمِ اللَّهِ الرَّحْمَانِ الرَّحِيمِ"
```
