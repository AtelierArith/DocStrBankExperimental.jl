```
sort!(v; alg::Algorithm=defalg(v), lt=isless, by=identity, rev::Bool=false, order::Ordering=Forward)
```

Sortiere den Vektor `v` in-place. Standardmäßig wird ein stabiles Algorithmus verwendet: die Reihenfolge der Elemente, die gleich sind, bleibt erhalten. Ein spezifischer Algorithmus kann über das Schlüsselwort `alg` ausgewählt werden (siehe [Sortieralgorithmen](@ref) für verfügbare Algorithmen).

Die Elemente werden zuerst mit der Funktion `by` transformiert und dann entweder gemäß der Funktion `lt` oder der Reihenfolge `order` verglichen. Schließlich wird die resultierende Reihenfolge umgekehrt, wenn `rev=true` (dies bewahrt die Vorwärtsstabilität: Elemente, die gleich sind, werden nicht umgekehrt). Die aktuelle Implementierung wendet die `by`-Transformation vor jedem Vergleich an, anstatt einmal pro Element.

Das Übergeben eines `lt`, das nicht `isless` ist, zusammen mit einer `order`, die nicht [`Base.Order.Forward`](@ref) oder [`Base.Order.Reverse`](@ref) ist, ist nicht erlaubt; andernfalls sind alle Optionen unabhängig und können in allen möglichen Kombinationen zusammen verwendet werden. Beachte, dass `order` auch eine "by"-Transformation enthalten kann, in diesem Fall wird sie nach der mit dem Schlüsselwort `by` definierten angewendet. Für weitere Informationen zu `order`-Werten siehe die Dokumentation zu [Alternativen Reihenfolgen](@ref).

Die Beziehungen zwischen zwei Elementen sind wie folgt definiert (mit "weniger" und "größer" vertauscht, wenn `rev=true`):

  * `x` ist kleiner als `y`, wenn `lt(by(x), by(y))` (oder `Base.Order.lt(order, by(x), by(y))`) wahr ergibt.
  * `x` ist größer als `y`, wenn `y` kleiner als `x` ist.
  * `x` und `y` sind äquivalent, wenn keiner kleiner als der andere ist ("nicht vergleichbar" wird manchmal als Synonym für "äquivalent" verwendet).

Das Ergebnis von `sort!` ist so sortiert, dass jedes Element größer oder äquivalent zum vorherigen ist.

Die `lt`-Funktion muss eine strikte schwache Ordnung definieren, das heißt, sie muss

  * irreflexiv sein: `lt(x, x)` ergibt immer `false`,
  * asymmetrisch sein: wenn `lt(x, y)` `true` ergibt, dann ergibt `lt(y, x)` `false`,
  * transitiv sein: `lt(x, y) && lt(y, z)` impliziert `lt(x, z)`,
  * transitiv in der Äquivalenz sein: `!lt(x, y) && !lt(y, x)` und `!lt(y, z) && !lt(z, y)` implizieren zusammen `!lt(x, z) && !lt(z, x)`. Mit anderen Worten: wenn `x` und `y` äquivalent sind und `y` und `z` äquivalent sind, dann müssen `x` und `z` äquivalent sein.

Zum Beispiel ist `<` eine gültige `lt`-Funktion für `Int`-Werte, aber `≤` ist es nicht: es verletzt die Irreflexivität. Für `Float64`-Werte ist sogar `<` ungültig, da es die vierte Bedingung verletzt: `1.0` und `NaN` sind äquivalent und ebenso `NaN` und `2.0`, aber `1.0` und `2.0` sind nicht äquivalent.

Siehe auch [`sort`](@ref), [`sortperm`](@ref), [`sortslices`](@ref), [`partialsort!`](@ref), [`partialsortperm`](@ref), [`issorted`](@ref), [`searchsorted`](@ref), [`insorted`](@ref), [`Base.Order.ord`](@ref).

# Beispiele

```jldoctest
julia> v = [3, 1, 2]; sort!(v); v
3-element Vector{Int64}:
 1
 2
 3

julia> v = [3, 1, 2]; sort!(v, rev = true); v
3-element Vector{Int64}:
 3
 2
 1

julia> v = [(1, "c"), (3, "a"), (2, "b")]; sort!(v, by = x -> x[1]); v
3-element Vector{Tuple{Int64, String}}:
 (1, "c")
 (2, "b")
 (3, "a")

julia> v = [(1, "c"), (3, "a"), (2, "b")]; sort!(v, by = x -> x[2]); v
3-element Vector{Tuple{Int64, String}}:
 (3, "a")
 (2, "b")
 (1, "c")

julia> sort(0:3, by=x->x-2, order=Base.Order.By(abs)) # dasselbe wie sort(0:3, by=abs(x->x-2))
4-element Vector{Int64}:
 2
 1
 3
 0

julia> sort([2, NaN, 1, NaN, 3]) # korrekte Sortierung mit standard lt=isless
5-element Vector{Float64}:
   1.0
   2.0
   3.0
 NaN
 NaN

julia> sort([2, NaN, 1, NaN, 3], lt=<) # falsche Sortierung aufgrund ungültigem lt. Dieses Verhalten ist undefiniert.
5-element Vector{Float64}:
   2.0
 NaN
   1.0
 NaN
   3.0
```
