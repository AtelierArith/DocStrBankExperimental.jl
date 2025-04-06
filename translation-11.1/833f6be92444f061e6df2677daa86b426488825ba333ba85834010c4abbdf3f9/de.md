# Bounds checking

Wie viele moderne Programmiersprachen verwendet Julia eine Grenzprüfung, um die Programmsicherheit beim Zugriff auf Arrays zu gewährleisten. In engen inneren Schleifen oder anderen leistungskritischen Situationen möchten Sie möglicherweise diese Grenzprüfungen überspringen, um die Laufzeitleistung zu verbessern. Zum Beispiel kann Ihr Schleifenrumpf keine Verzweigungen enthalten, um vektorisierte (SIMD) Anweisungen auszugeben, und kann daher keine Grenzprüfungen enthalten. Folglich enthält Julia ein `@inbounds(...)` Makro, um dem Compiler zu sagen, dass er solche Grenzprüfungen innerhalb des angegebenen Blocks überspringen soll. Benutzerdefinierte Array-Typen können das `@boundscheck(...)` Makro verwenden, um kontextsensitive Codeauswahl zu erreichen.

## Eliding bounds checks

Das `@boundscheck(...)`-Makro kennzeichnet Codeblöcke, die eine Bereichsüberprüfung durchführen. Wenn solche Blöcke in einen `@inbounds(...)`-Block eingefügt werden, kann der Compiler diese Blöcke entfernen. Der Compiler entfernt den `@boundscheck`-Block *nur wenn er in die aufrufende Funktion eingefügt wird*. Zum Beispiel könnten Sie die Methode `sum` wie folgt schreiben:

```julia
function sum(A::AbstractArray)
    r = zero(eltype(A))
    for i in eachindex(A)
        @inbounds r += A[i]
    end
    return r
end
```

Mit einem benutzerdefinierten array-ähnlichen Typ `MyArray`, der:

```julia
@inline getindex(A::MyArray, i::Real) = (@boundscheck checkbounds(A, i); A.data[to_index(i)])
```

Dann wird, wenn `getindex` in `sum` inline gesetzt wird, der Aufruf von `checkbounds(A, i)` weggelassen. Wenn Ihre Funktion mehrere Ebenen der Inline-Setzung enthält, werden nur `@boundscheck`-Blöcke, die höchstens eine Ebene tiefer in der Inline-Setzung liegen, eliminiert. Die Regel verhindert unbeabsichtigte Änderungen im Programmverhalten durch Code weiter oben im Stack.

### Caution!

Es ist einfach, versehentlich unsichere Operationen mit `@inbounds` offenzulegen. Sie könnten versucht sein, das obige Beispiel so zu schreiben als

```julia
function sum(A::AbstractArray)
    r = zero(eltype(A))
    for i in 1:length(A)
        @inbounds r += A[i]
    end
    return r
end
```

Welche stillschweigend von 1-basiertem Indexing ausgeht und daher unsicheren Speicherzugriff offenbart, wenn sie mit [`OffsetArrays`](@ref man-custom-indices) verwendet wird:

```julia-repl
julia> using OffsetArrays

julia> sum(OffsetArray([1, 2, 3], -10))
9164911648 # inconsistent results or segfault
```

Während die ursprüngliche Quelle des Fehlers hier `1:length(A)` ist, erhöht die Verwendung von `@inbounds` die Konsequenzen von einem Bereichsfehler zu einem weniger leicht erfassten und debugbaren unsicheren Speicherzugriff. Es ist oft schwierig oder unmöglich zu beweisen, dass eine Methode, die `@inbounds` verwendet, sicher ist, daher muss man die Vorteile von Leistungsverbesserungen gegen das Risiko von Segfaults und stillschweigenden Fehlverhalten abwägen, insbesondere in öffentlich zugänglichen APIs.

## Propagating inbounds

Es kann bestimmte Szenarien geben, in denen Sie aus Gründen der Code-Organisation mehr als eine Schicht zwischen den `@inbounds`- und `@boundscheck`-Deklarationen wünschen. Zum Beispiel haben die Standard-`getindex`-Methoden die Kette `getindex(A::AbstractArray, i::Real)` ruft `getindex(IndexStyle(A), A, i)` auf, das ruft `_getindex(::IndexLinear, A, i)` auf.

Um die Regel "eine Schicht der Inline-Ersetzung" zu überschreiben, kann eine Funktion mit [`Base.@propagate_inbounds`](@ref) markiert werden, um einen Inbounds-Kontext (oder Out-of-Bounds-Kontext) durch eine zusätzliche Schicht der Inline-Ersetzung zu propagieren.

## The bounds checking call hierarchy

Die gesamte Hierarchie ist:

  * `checkbounds(A, I...)` die aufruft

      * `checkbounds(Bool, A, I...)` die aufruft

          * `checkbounds_indices(Bool, axes(A), I)` das rekursiv aufruft

              * `checkindex` für jede Dimension

Hier ist `A` das Array, und `I` enthält die "angeforderten" Indizes. `axes(A)` gibt ein Tupel der "erlaubten" Indizes von `A` zurück.

`checkbounds(A, I...)` wirft einen Fehler, wenn die Indizes ungültig sind, während `checkbounds(Bool, A, I...)` in diesem Fall `false` zurückgibt. `checkbounds_indices` verwirft alle Informationen über das Array außer dem `axes`-Tupel und führt einen reinen Vergleich von Indizes gegen Indizes durch: Dies ermöglicht es relativ wenigen kompilierten Methoden, eine riesige Vielfalt von Array-Typen zu bedienen. Indizes werden als Tupel angegeben und normalerweise in einer 1-1-Form verglichen, wobei einzelne Dimensionen durch den Aufruf einer anderen wichtigen Funktion, `checkindex`, behandelt werden: typischerweise,

```julia
checkbounds_indices(Bool, (IA1, IA...), (I1, I...)) = checkindex(Bool, IA1, I1) &
                                                      checkbounds_indices(Bool, IA, I)
```

so `checkindex` überprüft eine einzelne Dimension. Alle diese Funktionen, einschließlich der nicht exportierten `checkbounds_indices`, haben Docstrings, die mit `?` zugänglich sind.

Wenn Sie die Grenzüberprüfung für einen bestimmten Arraytyp anpassen müssen, sollten Sie `checkbounds(Bool, A, I...)` spezialisieren. In den meisten Fällen sollten Sie jedoch in der Lage sein, sich auf `checkbounds_indices` zu verlassen, solange Sie nützliche `axes` für Ihren Arraytyp bereitstellen.

Wenn Sie neuartige Indextypen haben, sollten Sie zunächst in Betracht ziehen, `checkindex` zu spezialisieren, das einen einzelnen Index für eine bestimmte Dimension eines Arrays behandelt. Wenn Sie einen benutzerdefinierten mehrdimensionalen Indextyp (ähnlich wie `CartesianIndex`) haben, müssen Sie möglicherweise in Betracht ziehen, `checkbounds_indices` zu spezialisieren.

Beachten Sie, dass diese Hierarchie so gestaltet wurde, dass die Wahrscheinlichkeit von Methodenambiguitäten verringert wird. Wir versuchen, `checkbounds` als den Ort zu gestalten, an dem auf den Array-Typ spezialisiert wird, und versuchen, Spezialisierungen auf Indextypen zu vermeiden; umgekehrt ist `checkindex` nur für die Spezialisierung auf den Indextyp gedacht (insbesondere das letzte Argument).

## Emit bounds checks

Julia kann mit `--check-bounds={yes|no|auto}` gestartet werden, um Bereichsprüfungen immer, nie oder entsprechend den `@inbounds`-Deklarationen auszugeben.
