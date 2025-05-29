```
dediac(s::String)
```

Dediacritize the input `String` object.

# Examples

```julia-repl
julia> bw_basmala = "bisomi {ll~ahi {lr~aHoma`ni {lr~aHiymi"
julia> dediac(bw_basmala)
"bsm {llh {lrHmn {lrHym"
julia> dediac(arabic(bw_basmala))
"بسم ٱلله ٱلرحمن ٱلرحيم"
```
