```
normalize(s::String)
```

Normalize a Arabic or Buckwalter `String` characters.

# Examples

```julia-repl
julia> normalize("بِسْمِ ٱللَّهِ ٱلرَّحْمَٰنِ ٱلرَّحِيمِ")
"بِسْمِ اللَّهِ الرَّحْمَانِ الرَّحِيمِ"
```
