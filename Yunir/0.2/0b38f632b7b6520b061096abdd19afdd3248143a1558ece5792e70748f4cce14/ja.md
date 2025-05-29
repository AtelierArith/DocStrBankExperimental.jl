```
normalize(s::String, char::Symbol)
```

特定のアラビア語またはバクワルターの `String` 文字 (`chars`) を正規化します。

# 例

```julia-repl
julia> ar_basmala = "بِسْمِ ٱللَّهِ ٱلرَّحْمَٰنِ ٱلرَّحِيمِ"
julia> normalize(ar_basmala, :alif_khanjareeya) === "بِسْمِ ٱللَّهِ ٱلرَّحْمَانِ ٱلرَّحِيمِ"
```
