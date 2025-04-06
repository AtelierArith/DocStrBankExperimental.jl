```
AbstractIrrational <: Real
```

Zahlentyp, der einen exakten irrationalen Wert darstellt, der in arithmetischen Operationen mit anderen numerischen Größen automatisch auf die richtige Präzision gerundet wird.

Untertypen `MyIrrational <: AbstractIrrational` sollten mindestens `==(::MyIrrational, ::MyIrrational)`, `hash(x::MyIrrational, h::UInt)` und `convert(::Type{F}, x::MyIrrational) where {F <: Union{BigFloat,Float32,Float64}}` implementieren.

Wenn ein Untertyp verwendet wird, um Werte darzustellen, die gelegentlich rational sein können (z. B. ein Quadratwurzeltyp, der `√n` für ganze Zahlen `n` darstellt, gibt ein rationales Ergebnis zurück, wenn `n` eine perfekte Quadratzahl ist), sollte er auch `isinteger`, `iszero`, `isone` und `==` mit `Real`-Werten implementieren (da all dies standardmäßig `false` für `AbstractIrrational`-Typen ist) sowie [`hash`](@ref) definieren, um dem entsprechenden `Rational` zu entsprechen.
