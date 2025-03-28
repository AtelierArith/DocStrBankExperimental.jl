```
Sampler(rng, x, repetition = Val(Inf))
```

Gibt ein Sampler-Objekt zurück, das verwendet werden kann, um zufällige Werte aus `rng` für `x` zu generieren.

Wenn `sp = Sampler(rng, x, repetition)` ist, wird `rand(rng, sp)` verwendet, um zufällige Werte zu ziehen, und sollte entsprechend definiert werden.

`repetition` kann `Val(1)` oder `Val(Inf)` sein und sollte als Vorschlag für die Entscheidung über die Menge an Vorberechnung verwendet werden, falls zutreffend.

[`Random.SamplerType`](@ref) und [`Random.SamplerTrivial`](@ref) sind Standardrückfalloptionen für *Typen* und *Werte* respektive. [`Random.SamplerSimple`](@ref) kann verwendet werden, um vorab berechnete Werte zu speichern, ohne zusätzliche Typen nur für diesen Zweck zu definieren. ```
