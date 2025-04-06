```
IndexLinear()
```

Untertyp von [`IndexStyle`](@ref), der verwendet wird, um Arrays zu beschreiben, die optimal mit einem linearen Index indiziert werden.

Ein lineares Indizierungsstil verwendet einen ganzzahligen Index, um die Position im Array zu beschreiben (auch wenn es sich um ein mehrdimensionales Array handelt), und die Spalten-Hauptordnung wird verwendet, um die Elemente effizient zuzugreifen. Das bedeutet, dass die Anforderung von [`eachindex`](@ref) von einem Array, das `IndexLinear` ist, einen einfachen eindimensionalen Bereich zurückgibt, auch wenn es mehrdimensional ist.

Ein benutzerdefiniertes Array, das seinen `IndexStyle` als `IndexLinear` meldet, muss nur die Indizierung (und die indizierte Zuweisung) mit einem einzelnen `Int`-Index implementieren; alle anderen Indizierungsanfragen — einschließlich mehrdimensionaler Zugriffe — werden auf den linearen Index neu berechnet. Zum Beispiel, wenn `A` eine `2×3` benutzerdefinierte Matrix mit linearer Indizierung wäre und wir `A[1, 3]` referenzieren, würde dies auf den entsprechenden linearen Index neu berechnet und `A[5]` aufgerufen, da `1 + 2*(3 - 1) = 5`.

Siehe auch [`IndexCartesian`](@ref).
