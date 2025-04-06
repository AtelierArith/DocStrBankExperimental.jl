```
DateTime(dt::AbstractString, df::DateFormat=ISODateTimeFormat) -> DateTime
```

Konstruiere ein `DateTime`, indem der `dt` Datumszeit-String gemäß dem Muster im [`DateFormat`](@ref) Objekt geparst wird, oder dateformat"yyyy-mm-dd\THH:MM:SS.s", wenn weggelassen.

Ähnlich wie `DateTime(::AbstractString, ::AbstractString)`, aber effizienter, wenn wiederholt ähnlich formatierte Datumszeit-Strings mit einem vorab erstellten `DateFormat` Objekt geparst werden.
