# [Missing Values](@id missing)

Julia bietet Unterstützung für die Darstellung fehlender Werte im statistischen Sinne. Dies gilt für Situationen, in denen kein Wert für eine Variable in einer Beobachtung verfügbar ist, aber theoretisch ein gültiger Wert existiert. Fehlende Werte werden über das [`missing`](@ref) Objekt dargestellt, das die Singleton-Instanz des Typs [`Missing`](@ref) ist. `missing` ist gleichwertig mit [`NULL` in SQL](https://en.wikipedia.org/wiki/NULL_(SQL)) und [`NA` in R](https://cran.r-project.org/doc/manuals/r-release/R-lang.html#NA-handling) und verhält sich in den meisten Situationen wie sie.

## Propagation of Missing Values

`fehlende` Werte *propagieren* sich automatisch, wenn sie an standardmäßige mathematische Operatoren und Funktionen übergeben werden. Für diese Funktionen führt die Unsicherheit über den Wert eines der Operanden zu Unsicherheit über das Ergebnis. In der Praxis bedeutet dies, dass eine mathematische Operation, die einen `fehlenden` Wert beinhaltet, im Allgemeinen `fehlend` zurückgibt:

```jldoctest
julia> missing + 1
missing

julia> "a" * missing
missing

julia> abs(missing)
missing
```

Da `missing` ein normales Julia-Objekt ist, funktioniert diese Propagierungsregel nur für Funktionen, die sich entschieden haben, dieses Verhalten zu implementieren. Dies kann erreicht werden durch:

  * eine spezifische Methode hinzufügen, die für Argumente vom Typ `Missing` definiert ist,
  * Argumente dieses Typs akzeptieren und sie an Funktionen weitergeben, die sie propagieren (wie standardmäßige mathematische Operatoren).

Pakete sollten überlegen, ob es sinnvoll ist, fehlende Werte zu propagieren, wenn neue Funktionen definiert werden, und die Methoden entsprechend definieren, falls dies der Fall ist. Das Übergeben eines `missing` Wertes an eine Funktion, die keine Methode hat, die Argumente vom Typ `Missing` akzeptiert, wirft eine [`MethodError`](@ref), genau wie bei jedem anderen Typ.

Funktionen, die `missing`-Werte nicht propagieren, können dazu gebracht werden, dies zu tun, indem man sie in die `passmissing`-Funktion einwickelt, die im [Missings.jl](https://github.com/JuliaData/Missings.jl)-Paket bereitgestellt wird. Zum Beispiel wird `f(x)` zu `passmissing(f)(x)`.

## Equality and Comparison Operators

Standardgleichheits- und Vergleichsoperatoren folgen der oben dargestellten Propagationsregel: Wenn einer der Operanden `fehlend` ist, ist das Ergebnis `fehlend`. Hier sind einige Beispiele:

```jldoctest
julia> missing == 1
missing

julia> missing == missing
missing

julia> missing < 1
missing

julia> 2 >= missing
missing
```

Insbesondere ist zu beachten, dass `missing == missing` `missing` zurückgibt, sodass `==` nicht verwendet werden kann, um zu testen, ob ein Wert fehlt. Um zu testen, ob `x` `missing` ist, verwenden Sie [`ismissing(x)`](@ref).

Besondere Vergleichsoperatoren [`isequal`](@ref) und [`===`](@ref) sind Ausnahmen von der Propagierungsregel. Sie geben immer einen `Bool`-Wert zurück, selbst in Anwesenheit von `missing`-Werten, wobei `missing` als gleich zu `missing` und als unterschiedlich von jedem anderen Wert betrachtet wird. Sie können daher verwendet werden, um zu testen, ob ein Wert `missing` ist:

```jldoctest
julia> missing === 1
false

julia> isequal(missing, 1)
false

julia> missing === missing
true

julia> isequal(missing, missing)
true
```

The [`isless`](@ref) operator is another exception: `missing` is considered as greater than any other value. This operator is used by [`sort!`](@ref), which therefore places `missing` values after all other values:

```jldoctest
julia> isless(1, missing)
true

julia> isless(missing, Inf)
false

julia> isless(missing, missing)
false
```

## Logical operators

Logische (oder boolesche) Operatoren [`|`](@ref), [`&`](@ref) und [`xor`](@ref) sind ein weiterer Sonderfall, da sie nur `fehlende` Werte propagieren, wenn dies logisch erforderlich ist. Bei diesen Operatoren hängt es von der jeweiligen Operation ab, ob das Ergebnis ungewiss ist oder nicht. Dies folgt den gut etablierten Regeln von [*three-valued logic*](https://en.wikipedia.org/wiki/Three-valued_logic), die z.B. durch `NULL` in SQL und `NA` in R implementiert sind. Diese abstrakte Definition entspricht einem relativ natürlichen Verhalten, das am besten durch konkrete Beispiele erklärt werden kann.

Lassen Sie uns dieses Prinzip mit dem logischen "oder"-Operator [`|`](@ref) veranschaulichen. Nach den Regeln der booleschen Logik hat, wenn einer der Operanden `true` ist, der Wert des anderen Operanden keinen Einfluss auf das Ergebnis, das immer `true` sein wird:

```jldoctest
julia> true | true
true

julia> true | false
true

julia> false | true
true
```

Basierend auf dieser Beobachtung können wir schließen, dass, wenn einer der Operanden `true` und der andere `missing` ist, wir wissen, dass das Ergebnis `true` ist, trotz der Unsicherheit über den tatsächlichen Wert eines der Operanden. Hätten wir den tatsächlichen Wert des zweiten Operanden beobachten können, könnte dieser nur `true` oder `false` sein, und in beiden Fällen wäre das Ergebnis `true`. Daher propagiert in diesem speziellen Fall die Fehlendeheit *nicht*:

```jldoctest
julia> true | missing
true

julia> missing | true
true
```

Im Gegenteil, wenn einer der Operanden `false` ist, kann das Ergebnis entweder `true` oder `false` sein, abhängig vom Wert des anderen Operanden. Daher muss, wenn dieser Operand `fehlend` ist, das Ergebnis ebenfalls `fehlend` sein:

```jldoctest
julia> false | true
true

julia> true | false
true

julia> false | false
false

julia> false | missing
missing

julia> missing | false
missing
```

Das Verhalten des logischen "und" Operators [`&`](@ref) ist ähnlich dem des `|` Operators, mit dem Unterschied, dass Fehlende Werte nicht propagiert werden, wenn einer der Operanden `false` ist. Zum Beispiel, wenn dies der Fall beim ersten Operanden ist:

```jldoctest
julia> false & false
false

julia> false & true
false

julia> false & missing
false
```

Andererseits propagiert die Fehlendheit, wenn einer der Operanden `true` ist, zum Beispiel der erste:

```jldoctest
julia> true & true
true

julia> true & false
false

julia> true & missing
missing
```

Schließlich propagiert der logische Operator "exklusiv oder" [`xor`](@ref) immer `fehlende` Werte, da beide Operanden immer einen Einfluss auf das Ergebnis haben. Beachten Sie auch, dass der Negationsoperator [`!`](@ref) `fehlende` zurückgibt, wenn der Operand `fehlend` ist, genau wie andere unäre Operatoren.

## Control Flow and Short-Circuiting Operators

Steuerflussoperatoren, einschließlich [`if`](@ref), [`while`](@ref) und der [ternary operator](@ref man-conditional-evaluation) `x ? y : z`, erlauben keine fehlenden Werte. Dies liegt an der Ungewissheit darüber, ob der tatsächliche Wert `true` oder `false` wäre, wenn wir ihn beobachten könnten. Das bedeutet, dass wir nicht wissen, wie sich das Programm verhalten sollte. In diesem Fall wird ein [`TypeError`](@ref) ausgelöst, sobald ein `missing` Wert in diesem Kontext auftritt:

```jldoctest
julia> if missing
           println("here")
       end
ERROR: TypeError: non-boolean (Missing) used in boolean context
```

For the same reason, contrary to logical operators presented above, the short-circuiting boolean operators [`&&`](@ref) and [`||`](@ref) do not allow for `missing` values in situations where the value of the operand determines whether the next operand is evaluated or not. For example:

```jldoctest
julia> missing || false
ERROR: TypeError: non-boolean (Missing) used in boolean context

julia> missing && false
ERROR: TypeError: non-boolean (Missing) used in boolean context

julia> true && missing && false
ERROR: TypeError: non-boolean (Missing) used in boolean context
```

Im Gegensatz dazu wird kein Fehler ausgelöst, wenn das Ergebnis ohne die `missing`-Werte bestimmt werden kann. Dies ist der Fall, wenn der Code vor der Auswertung des `missing`-Operands kurzgeschlossen wird und wenn der `missing`-Operand der letzte ist:

```jldoctest
julia> true && missing
missing

julia> false && missing
false
```

## Arrays With Missing Values

Arrays, die fehlende Werte enthalten, können wie andere Arrays erstellt werden:

```jldoctest
julia> [1, missing]
2-element Vector{Union{Missing, Int64}}:
 1
  missing
```

Wie dieses Beispiel zeigt, ist der Elementtyp solcher Arrays `Union{Missing, T}`, wobei `T` der Typ der nicht fehlenden Werte ist. Dies spiegelt wider, dass die Array-Einträge entweder vom Typ `T` (hier `Int64`) oder vom Typ `Missing` sein können. Diese Art von Array verwendet eine effiziente Speicherverwaltung, die einem `Array{T}` entspricht, das die tatsächlichen Werte hält, kombiniert mit einem `Array{UInt8}`, das den Typ des Eintrags angibt (d.h. ob er `Missing` oder `T` ist).

Arrays, die fehlende Werte zulassen, können mit der Standard-Syntax erstellt werden. Verwenden Sie `Array{Union{Missing, T}}(missing, dims)`, um Arrays zu erstellen, die mit fehlenden Werten gefüllt sind:

```jldoctest
julia> Array{Union{Missing, String}}(missing, 2, 3)
2×3 Matrix{Union{Missing, String}}:
 missing  missing  missing
 missing  missing  missing
```

!!! note
    Die Verwendung von `undef` oder `ähnlichem` kann derzeit ein Array mit `missing` füllen, aber dies ist nicht der richtige Weg, um ein solches Array zu erhalten. Verwenden Sie stattdessen einen `missing`-Konstruktor, wie oben gezeigt.


Ein Array mit einem Elementtyp, der `missing`-Einträge erlaubt (z. B. `Vector{Union{Missing, T}}`), das keine `missing`-Einträge enthält, kann in einen Arraytyp umgewandelt werden, der keine `missing`-Einträge erlaubt (z. B. `Vector{T}`), indem [`convert`](@ref) verwendet wird. Wenn das Array `missing`-Werte enthält, wird während der Umwandlung ein `MethodError` ausgelöst:

```jldoctest
julia> x = Union{Missing, String}["a", "b"]
2-element Vector{Union{Missing, String}}:
 "a"
 "b"

julia> convert(Array{String}, x)
2-element Vector{String}:
 "a"
 "b"

julia> y = Union{Missing, String}[missing, "b"]
2-element Vector{Union{Missing, String}}:
 missing
 "b"

julia> convert(Array{String}, y)
ERROR: MethodError: Cannot `convert` an object of type Missing to an object of type String
```

## Skipping Missing Values

Da `missing`-Werte mit standardmäßigen mathematischen Operatoren propagieren, geben Reduktionsfunktionen `missing` zurück, wenn sie auf Arrays angewendet werden, die fehlende Werte enthalten:

```jldoctest
julia> sum([1, missing])
missing
```

In dieser Situation verwenden Sie die [`skipmissing`](@ref)-Funktion, um fehlende Werte zu überspringen:

```jldoctest
julia> sum(skipmissing([1, missing]))
1
```

Diese Hilfsfunktion gibt einen Iterator zurück, der `fehlende` Werte effizient herausfiltert. Sie kann daher mit jeder Funktion verwendet werden, die Iteratoren unterstützt:

```jldoctest skipmissing
julia> x = skipmissing([3, missing, 2, 1])
skipmissing(Union{Missing, Int64}[3, missing, 2, 1])

julia> maximum(x)
3

julia> sum(x)
6

julia> mapreduce(sqrt, +, x)
4.146264369941973
```

Objekte, die durch den Aufruf von `skipmissing` auf einem Array erstellt wurden, können mit Indizes aus dem übergeordneten Array indiziert werden. Indizes, die fehlenden Werten entsprechen, sind für diese Objekte nicht gültig, und es wird ein Fehler ausgegeben, wenn versucht wird, sie zu verwenden (sie werden auch von `keys` und `eachindex` übersprungen):

```jldoctest skipmissing
julia> x[1]
3

julia> x[2]
ERROR: MissingException: the value at index (2,) is missing
[...]
```

Dies ermöglicht es Funktionen, die auf Indizes arbeiten, in Kombination mit `skipmissing` zu funktionieren. Dies gilt insbesondere für Such- und Findefunktionen. Diese Funktionen geben Indizes zurück, die für das Objekt, das von `skipmissing` zurückgegeben wird, gültig sind, und sind auch die Indizes der übereinstimmenden Einträge *im übergeordneten Array*:

```jldoctest skipmissing
julia> findall(==(1), x)
1-element Vector{Int64}:
 4

julia> findfirst(!iszero, x)
1

julia> argmax(x)
1
```

Verwenden Sie [`collect`](@ref), um nicht `fehlende` Werte zu extrahieren und sie in einem Array zu speichern:

```jldoctest skipmissing
julia> collect(x)
3-element Vector{Int64}:
 3
 2
 1
```

## Logical Operations on Arrays

Die oben beschriebene dreiwertige Logik für logische Operatoren wird auch von logischen Funktionen angewendet, die auf Arrays angewendet werden. Daher geben Array-Gleichheitstests mit dem [`==`](@ref) Operator `missing` zurück, wann immer das Ergebnis nicht bestimmt werden kann, ohne den tatsächlichen Wert des `missing` Eintrags zu kennen. In der Praxis bedeutet dies, dass `missing` zurückgegeben wird, wenn alle nicht fehlenden Werte der verglichenen Arrays gleich sind, aber eines oder beide Arrays fehlende Werte enthalten (möglicherweise an unterschiedlichen Positionen):

```jldoctest
julia> [1, missing] == [2, missing]
false

julia> [1, missing] == [1, missing]
missing

julia> [1, 2, missing] == [1, missing, 2]
missing
```

Was einzelne Werte betrifft, verwenden Sie [`isequal`](@ref), um `fehlende` Werte als gleichwertig zu anderen `fehlenden` Werten zu behandeln, jedoch unterschiedlich von nicht fehlenden Werten:

```jldoctest
julia> isequal([1, missing], [1, missing])
true

julia> isequal([1, 2, missing], [1, missing, 2])
false
```

Funktionen [`any`](@ref) und [`all`](@ref) folgen ebenfalls den Regeln der dreiwertigen Logik. Daher geben sie `missing` zurück, wenn das Ergebnis nicht bestimmt werden kann:

```jldoctest
julia> all([true, missing])
missing

julia> all([false, missing])
false

julia> any([true, missing])
true

julia> any([false, missing])
missing
```
