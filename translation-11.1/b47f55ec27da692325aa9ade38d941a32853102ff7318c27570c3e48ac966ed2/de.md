```
randstring([rng=default_rng()], [chars], [len=8])
```

Erstellt einen zufälligen String der Länge `len`, der aus Zeichen von `chars` besteht, wobei `chars` standardmäßig aus Groß- und Kleinbuchstaben sowie den Ziffern 0-9 besteht. Das optionale Argument `rng` gibt einen Zufallszahlengenerator an, siehe [Random Numbers](@ref).

# Beispiele

```jldoctest
julia> Random.seed!(3); randstring()
"Lxz5hUwn"

julia> randstring(Xoshiro(3), 'a':'z', 6)
"iyzcsm"

julia> randstring("ACGT")
"TGCTCCTC"
```

!!! Hinweis     `chars` kann jede Sammlung von Zeichen sein, vom Typ `Char` oder `UInt8` (effizienter), vorausgesetzt, dass [`rand`](@ref) Zeichen zufällig daraus auswählen kann.
