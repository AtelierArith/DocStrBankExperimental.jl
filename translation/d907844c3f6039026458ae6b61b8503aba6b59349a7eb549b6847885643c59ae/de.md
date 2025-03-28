```
NamedTuple
```

`NamedTuple`s sind, wie der Name schon sagt, benannte [`Tuple`](@ref)s. Das heißt, sie sind eine tuple-ähnliche Sammlung von Werten, bei der jeder Eintrag einen eindeutigen Namen hat, der als [`Symbol`](@ref) dargestellt wird. Wie `Tuple`s sind `NamedTuple`s unveränderlich; weder die Namen noch die Werte können nach der Konstruktion vor Ort geändert werden.

Ein benanntes Tupel kann als Tupel-Literal mit Schlüsseln erstellt werden, z.B. `(a=1, b=2)`, oder als Tupel-Literal mit Semikolon nach der öffnenden Klammer, z.B. `(; a=1, b=2)` (diese Form akzeptiert auch programmgenerierte Namen, wie unten beschrieben), oder unter Verwendung eines `NamedTuple`-Typs als Konstruktor, z.B. `NamedTuple{(:a, :b)}((1,2))`.

Der Zugriff auf den Wert, der mit einem Namen in einem benannten Tupel verknüpft ist, kann mit der Feldzugriffs-Syntax erfolgen, z.B. `x.a`, oder unter Verwendung von [`getindex`](@ref), z.B. `x[:a]` oder `x[(:a, :b)]`. Ein Tupel der Namen kann mit [`keys`](@ref) erhalten werden, und ein Tupel der Werte kann mit [`values`](@ref) erhalten werden.

!!! note
    Die Iteration über `NamedTuple`s erzeugt die *Werte* ohne die Namen. (Siehe Beispiel unten.) Um über die Name-Wert-Paare zu iterieren, verwenden Sie die Funktion [`pairs`](@ref).


Das [`@NamedTuple`](@ref) Makro kann verwendet werden, um `NamedTuple`-Typen bequem zu deklarieren.

# Beispiele

```jldoctest
julia> x = (a=1, b=2)
(a = 1, b = 2)

julia> x.a
1

julia> x[:a]
1

julia> x[(:a,)]
(a = 1,)

julia> keys(x)
(:a, :b)

julia> values(x)
(1, 2)

julia> collect(x)
2-element Vector{Int64}:
 1
 2

julia> collect(pairs(x))
2-element Vector{Pair{Symbol, Int64}}:
 :a => 1
 :b => 2
```

In ähnlicher Weise, wie man Schlüsselwortargumente programmgesteuert definieren kann, kann ein benanntes Tupel erstellt werden, indem man Paare `name::Symbol => value` nach einem Semikolon innerhalb eines Tupel-Literals angibt. Diese und die `name=value`-Syntax können gemischt werden:

```jldoctest
julia> (; :a => 1, :b => 2, c=3)
(a = 1, b = 2, c = 3)
```

Die Name-Wert-Paare können auch bereitgestellt werden, indem ein benanntes Tupel oder ein beliebiger Iterator, der zweiwertige Sammlungen mit jeweils einem Symbol als erstem Wert erzeugt, gesplattet wird:

```jldoctest
julia> keys = (:a, :b, :c); values = (1, 2, 3);

julia> NamedTuple{keys}(values)
(a = 1, b = 2, c = 3)

julia> (; (keys .=> values)...)
(a = 1, b = 2, c = 3)

julia> nt1 = (a=1, b=2);

julia> nt2 = (c=3, d=4);

julia> (; nt1..., nt2..., b=20) # das finale b überschreibt den Wert von nt1
(a = 1, b = 20, c = 3, d = 4)

julia> (; zip(keys, values)...) # zip erzeugt Tupel wie (:a, 1)
(a = 1, b = 2, c = 3)
```

Wie bei Schlüsselwortargumenten implizieren Bezeichner und Punkt-Ausdrücke Namen:

```jldoctest
julia> x = 0
0

julia> t = (; x)
(x = 0,)

julia> (; t.x)
(x = 0,)
```

!!! compat "Julia 1.5"
    Implizite Namen aus Bezeichnern und Punkt-Ausdrücken sind seit Julia 1.5 verfügbar.


!!! compat "Julia 1.7"
    Die Verwendung von `getindex`-Methoden mit mehreren `Symbol`s ist seit Julia 1.7 verfügbar.

