```
Date(d::AbstractString, df::DateFormat=ISODateFormat) -> Date
```

Konstruiere ein `Date`, indem der Datumsstring `d` gemäß dem Muster des [`DateFormat`](@ref)-Objekts geparst wird, oder dateformat"yyyy-mm-dd", wenn weggelassen.

Ähnlich wie `Date(::AbstractString, ::AbstractString)`, aber effizienter, wenn wiederholt ähnlich formatierte Datumsstrings mit einem vorab erstellten `DateFormat`-Objekt geparst werden.
