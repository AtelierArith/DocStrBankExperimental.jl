```
Xoshiro(seed::Union{Integer, AbstractString})
Xoshiro()
```

Xoshiro256++ ist ein schneller Pseudorandomzahlengenerator, der von David Blackman und Sebastiano Vigna in "Scrambled Linear Pseudorandom Number Generators", ACM Trans. Math. Softw., 2021 beschrieben wurde. Die Referenzimplementierung ist verfügbar unter https://prng.di.unimi.it

Neben der hohen Geschwindigkeit hat Xoshiro einen kleinen Speicherbedarf, was es für Anwendungen geeignet macht, bei denen viele verschiedene Zufallszustände über längere Zeit gehalten werden müssen.

Julias Xoshiro-Implementierung hat einen Bulk-Generierungsmodus; dieser erzeugt neue virtuelle PRNGs aus dem Elternteil und verwendet SIMD, um parallel zu generieren (d.h. der Bulk-Stream besteht aus mehreren interleaved xoshiro-Instanzen). Die virtuellen PRNGs werden verworfen, sobald die Bulk-Anfrage bearbeitet wurde (und sollten keine Heap-Allokationen verursachen).

Wenn kein Seed bereitgestellt wird, wird ein zufällig generierter erstellt (unter Verwendung von Entropie aus dem System). Siehe die [`seed!`](@ref) Funktion zum Neusäen eines bereits vorhandenen `Xoshiro`-Objekts.

!!! compat "Julia 1.11"
    Das Übergeben eines negativen ganzzahligen Seeds erfordert mindestens Julia 1.11.


# Beispiele

```jldoctest
julia> using Random

julia> rng = Xoshiro(1234);

julia> x1 = rand(rng, 2)
2-element Vector{Float64}:
 0.32597672886359486
 0.5490511363155669

julia> rng = Xoshiro(1234);

julia> x2 = rand(rng, 2)
2-element Vector{Float64}:
 0.32597672886359486
 0.5490511363155669

julia> x1 == x2
true
```
