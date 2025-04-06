```
Time(t::AbstractString, df::DateFormat=ISOTimeFormat) -> Time
```

Konstruiere eine `Time`, indem der `t` Datumszeit-String gemäß dem Muster im [`DateFormat`](@ref) Objekt geparst wird, oder dateformat"HH:MM:SS.s", wenn weggelassen.

Ähnlich wie `Time(::AbstractString, ::AbstractString)`, aber effizienter, wenn wiederholt ähnlich formatierte Zeitstrings mit einem vorab erstellten `DateFormat` Objekt geparst werden.
