```
tokenize(s::String)
```

文字列入力 s をスペースでトークン化し、句読点もトークン化します。

```julia-repl
julia> ar_basmala = "بِسْمِ ٱللَّهِ ٱلرَّحْمَٰنِ ٱلرَّحِيمِ"
julia> tokenize(ar_basmala)
4-element Vector{String}:
 "بِسْمِ"
 "ٱللَّهِ"
 "ٱلرَّحْمَٰنِ"
 "ٱلرَّحِيمِ"
```
