```
@transliterator(symbl)
```

Fallback to the default `Buckwalter` transliterator.

```julia-repl
julia> @transliterator :default
julia> ar_basmala = "بِسْمِ ٱللَّهِ ٱلرَّحْمَٰنِ ٱلرَّحِيمِ"
julia> encode(ar_basmala)
"bisomi {ll~ahi {lr~aHoma`ni {lr~aHiymi"
```
