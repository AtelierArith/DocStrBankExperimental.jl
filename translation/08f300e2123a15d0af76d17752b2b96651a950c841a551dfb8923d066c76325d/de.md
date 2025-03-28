```
codeunit(s::AbstractString) -> Type{<:Union{UInt8, UInt16, UInt32}}
```

Gibt den Codeeinheitstyp des angegebenen Zeichenfolgenobjekts zurück. Für ASCII-, Latin-1- oder UTF-8-codierte Zeichenfolgen wäre dies `UInt8`; für UCS-2 und UTF-16 wäre es `UInt16`; für UTF-32 wäre es `UInt32`. Der Codeeinheitstyp muss nicht auf diese drei Typen beschränkt sein, aber es ist schwer, weit verbreitete Zeichenkodierungen zu finden, die nicht eine dieser Einheiten verwenden. `codeunit(s)` ist dasselbe wie `typeof(codeunit(s,1))`, wenn `s` eine nicht leere Zeichenfolge ist.

Siehe auch [`ncodeunits`](@ref).
