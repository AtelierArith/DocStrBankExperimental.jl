```
IndexCartesian()
```

Untertyp von [`IndexStyle`](@ref), der verwendet wird, um Arrays zu beschreiben, die optimal mit einem kartesischen Index indiziert werden. Dies ist der Standard für neue benutzerdefinierte [`AbstractArray`](@ref) Untertypen.

Ein kartesischer Indizierungsstil verwendet mehrere ganzzahlige Indizes, um die Position in einem mehrdimensionalen Array zu beschreiben, wobei genau ein Index pro Dimension verwendet wird. Das bedeutet, dass die Anforderung von [`eachindex`](@ref) von einem Array, das `IndexCartesian` ist, einen Bereich von [`CartesianIndices`](@ref) zurückgibt.

Ein `N`-dimensionales benutzerdefiniertes Array, das seinen `IndexStyle` als `IndexCartesian` meldet, muss die Indizierung (und indizierte Zuweisung) mit genau `N` `Int`-Indizes implementieren; alle anderen Indizierungsanfragen — einschließlich linearer Indizierung — werden auf die entsprechende kartesische Position umgerechnet. Zum Beispiel, wenn `A` eine `2×3` benutzerdefinierte Matrix mit kartesischer Indizierung wäre und wir `A[5]` referenzieren, würde dies auf den entsprechenden kartesischen Index umgerechnet und `A[1, 3]` aufgerufen, da `5 = 1 + 2*(3 - 1)`.

Es ist erheblich teurer, kartesische Indizes aus einem linearen Index zu berechnen, als umgekehrt. Die erste Operation erfordert eine Division — eine sehr kostspielige Operation — während die letztere nur Multiplikation und Addition verwendet und im Wesentlichen kostenlos ist. Diese Asymmetrie bedeutet, dass es viel kostspieliger ist, die lineare Indizierung mit einem `IndexCartesian`-Array zu verwenden, als die kartesische Indizierung mit einem `IndexLinear`-Array zu verwenden.

Siehe auch [`IndexLinear`](@ref).
