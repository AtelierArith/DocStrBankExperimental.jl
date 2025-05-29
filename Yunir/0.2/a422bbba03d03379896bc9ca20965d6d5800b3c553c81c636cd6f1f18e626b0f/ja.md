```
arabic(s::String[, encoder::AbstractEncoder])
```

`String`オブジェクトをアラビア文字にエンコードします。`@transliterator`から生成されたカスタム`encoder`を提供できますが、デフォルトは`Buckwalter`です。

# 例

```julia-repl
julia> bw_basmala = "bisomi {ll~ahi {lr~aHoma`ni {lr~aHiymi"
julia> arabic(bw_basmala)
"بِسْمِ ٱللَّهِ ٱلرَّحْمَٰنِ ٱلرَّحِيمِ"
```
