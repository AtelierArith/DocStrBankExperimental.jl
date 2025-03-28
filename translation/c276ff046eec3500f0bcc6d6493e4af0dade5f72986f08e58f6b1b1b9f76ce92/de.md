# [Single- and multi-dimensional Arrays](@id man-multi-dim-arrays)

Julia, wie die meisten technischen Programmiersprachen, bietet eine erstklassige Array-Implementierung. Die meisten technischen Programmiersprachen legen viel Wert auf ihre Array-Implementierung auf Kosten anderer Container. Julia behandelt Arrays nicht auf besondere Weise. Die Array-Bibliothek ist fast vollständig in Julia selbst implementiert und erzielt ihre Leistung vom Compiler, genau wie jeder andere in Julia geschriebene Code. Daher ist es auch möglich, benutzerdefinierte Array-Typen zu definieren, indem man von [`AbstractArray`](@ref) erbt. Siehe die [manual section on the AbstractArray interface](@ref man-interface-array) für weitere Details zur Implementierung eines benutzerdefinierten Array-Typs.

Ein Array ist eine Sammlung von Objekten, die in einem mehrdimensionalen Gitter gespeichert sind. Null-dimensionale Arrays sind erlaubt, siehe [this FAQ entry](@ref faq-array-0dim). Im allgemeinsten Fall kann ein Array Objekte des Typs [`Any`](@ref) enthalten. Für die meisten rechnerischen Zwecke sollten Arrays Objekte eines spezifischeren Typs enthalten, wie z.B. [`Float64`](@ref) oder [`Int32`](@ref).

Im Allgemeinen erwartet Julia, im Gegensatz zu vielen anderen technischen Programmiersprachen, nicht, dass Programme für die Leistung in einem vektorisierenden Stil geschrieben werden. Der Compiler von Julia verwendet Typinferenz und generiert optimierten Code für skalare Array-Indizierung, was es ermöglicht, Programme in einem Stil zu schreiben, der bequem und lesbar ist, ohne die Leistung zu opfern und manchmal weniger Speicher zu verwenden.

In Julia sind alle Argumente für Funktionen [passed by sharing](https://en.wikipedia.org/wiki/Evaluation_strategy#Call_by_sharing) (d.h. durch Zeiger). Einige technische Programmiersprachen übergeben Arrays durch Wert, und während dies eine versehentliche Modifikation durch die aufrufenden Funktionen an einem Wert im Aufrufer verhindert, macht es das Vermeiden unerwünschter Kopien von Arrays schwierig. Nach Konvention zeigt ein Funktionsname, der mit einem `!` endet, an, dass er den Wert eines oder mehrerer seiner Argumente verändern oder zerstören wird (vergleiche zum Beispiel [`sort`](@ref) und [`sort!`](@ref)). Aufgerufene Funktionen müssen explizite Kopien erstellen, um sicherzustellen, dass sie Eingaben, die sie nicht ändern wollen, nicht modifizieren. Viele nicht-modifizierende Funktionen werden implementiert, indem eine Funktion mit demselben Namen und einem hinzugefügten `!` am Ende auf einer expliziten Kopie der Eingabe aufgerufen und diese Kopie zurückgegeben wird.

## Basic Functions

| Function               | Description                                                                      |
|:---------------------- |:-------------------------------------------------------------------------------- |
| [`eltype(A)`](@ref)    | the type of the elements contained in `A`                                        |
| [`length(A)`](@ref)    | the number of elements in `A`                                                    |
| [`ndims(A)`](@ref)     | the number of dimensions of `A`                                                  |
| [`size(A)`](@ref)      | a tuple containing the dimensions of `A`                                         |
| [`size(A,n)`](@ref)    | the size of `A` along dimension `n`                                              |
| [`axes(A)`](@ref)      | a tuple containing the valid indices of `A`                                      |
| [`axes(A,n)`](@ref)    | a range expressing the valid indices along dimension `n`                         |
| [`eachindex(A)`](@ref) | an efficient iterator for visiting each position in `A`                          |
| [`stride(A,k)`](@ref)  | the stride (linear index distance between adjacent elements) along dimension `k` |
| [`strides(A)`](@ref)   | a tuple of the strides in each dimension                                         |

## Construction and Initialization

Viele Funktionen zum Erstellen und Initialisieren von Arrays sind verfügbar. In der folgenden Liste solcher Funktionen können Aufrufe mit einem `dims...`-Argument entweder ein einzelnes Tupel von Dimensionsgrößen oder eine Reihe von Dimensionsgrößen als variable Anzahl von Argumenten annehmen. Die meisten dieser Funktionen akzeptieren auch einen ersten Eingabewert `T`, der den Elementtyp des Arrays darstellt. Wenn der Typ `T` weggelassen wird, wird er standardmäßig auf [`Float64`](@ref) gesetzt.

| Function                           | Description                                                                                                                                                                                                                                  |
|:---------------------------------- |:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [`Array{T}(undef, dims...)`](@ref) | an uninitialized dense [`Array`](@ref)                                                                                                                                                                                                       |
| [`zeros(T, dims...)`](@ref)        | an `Array` of all zeros                                                                                                                                                                                                                      |
| [`ones(T, dims...)`](@ref)         | an `Array` of all ones                                                                                                                                                                                                                       |
| [`trues(dims...)`](@ref)           | a [`BitArray`](@ref) with all values `true`                                                                                                                                                                                                  |
| [`falses(dims...)`](@ref)          | a `BitArray` with all values `false`                                                                                                                                                                                                         |
| [`reshape(A, dims...)`](@ref)      | an array containing the same data as `A`, but with different dimensions                                                                                                                                                                      |
| [`copy(A)`](@ref)                  | copy `A`                                                                                                                                                                                                                                     |
| [`deepcopy(A)`](@ref)              | copy `A`, recursively copying its elements                                                                                                                                                                                                   |
| [`similar(A, T, dims...)`](@ref)   | an uninitialized array of the same type as `A` (dense, sparse, etc.), but with the specified element type and dimensions. The second and third arguments are both optional, defaulting to the element type and dimensions of `A` if omitted. |
| [`reinterpret(T, A)`](@ref)        | an array with the same binary data as `A`, but with element type `T`                                                                                                                                                                         |
| [`rand(T, dims...)`](@ref)         | an `Array` with random, iid [^1] and uniformly distributed values. For floating point types `T`, the values lie in the half-open interval $[0, 1)$.                                                                                          |
| [`randn(T, dims...)`](@ref)        | an `Array` with random, iid and standard normally distributed values                                                                                                                                                                         |
| [`Matrix{T}(I, m, n)`](@ref)       | `m`-by-`n` identity matrix. Requires `using LinearAlgebra` for [`I`](@ref).                                                                                                                                                                  |
| [`range(start, stop, n)`](@ref)    | a range of `n` linearly spaced elements from `start` to `stop`                                                                                                                                                                               |
| [`fill!(A, x)`](@ref)              | fill the array `A` with the value `x`                                                                                                                                                                                                        |
| [`fill(x, dims...)`](@ref)         | an `Array` filled with the value `x`. In particular, `fill(x)` constructs a zero-dimensional `Array` containing `x`.                                                                                                                         |

[^1]: *iid*, independently and identically distributed.

Um die verschiedenen Möglichkeiten zu sehen, wie wir Dimensionen an diese Funktionen übergeben können, betrachten Sie die folgenden Beispiele:

```jldoctest
julia> zeros(Int8, 2, 3)
2×3 Matrix{Int8}:
 0  0  0
 0  0  0

julia> zeros(Int8, (2, 3))
2×3 Matrix{Int8}:
 0  0  0
 0  0  0

julia> zeros((2, 3))
2×3 Matrix{Float64}:
 0.0  0.0  0.0
 0.0  0.0  0.0
```

Hier ist `(2, 3)` ein [`Tuple`](@ref) und das erste Argument — der Elementtyp — ist optional und standardmäßig auf `Float64` gesetzt.

## [Array literals](@id man-array-literals)

Arrays können auch direkt mit eckigen Klammern erstellt werden; die Syntax `[A, B, C, ...]` erstellt ein eindimensionales Array (d.h. einen Vektor), das die durch Kommas getrennten Argumente als Elemente enthält. Der Elementtyp ([`eltype`](@ref)) des resultierenden Arrays wird automatisch durch die Typen der Argumente in den Klammern bestimmt. Wenn alle Argumente vom gleichen Typ sind, dann ist das sein `eltype`. Wenn sie alle einen gemeinsamen [promotion type](@ref conversion-and-promotion) haben, werden sie in diesen Typ umgewandelt, indem [`convert`](@ref) verwendet wird, und dieser Typ ist das `eltype` des Arrays. Andernfalls wird ein heterogenes Array erstellt, das alles halten kann — ein `Vector{Any}` — dies schließt das Literal `[]` ein, wenn keine Argumente angegeben sind. [Array literal can be typed](@ref man-array-typed-literal) mit der Syntax `T[A, B, C, ...]`, wobei `T` ein Typ ist.

```jldoctest
julia> [1, 2, 3] # An array of `Int`s
3-element Vector{Int64}:
 1
 2
 3

julia> promote(1, 2.3, 4//5) # This combination of Int, Float64 and Rational promotes to Float64
(1.0, 2.3, 0.8)

julia> [1, 2.3, 4//5] # Thus that's the element type of this Array
3-element Vector{Float64}:
 1.0
 2.3
 0.8

julia> Float32[1, 2.3, 4//5] # Specify element type manually
3-element Vector{Float32}:
 1.0
 2.3
 0.8

julia> []
Any[]
```

### [Concatenation](@id man-array-concatenation)

Wenn die Argumente in den eckigen Klammern durch einfache Semikolons (`;`) oder Zeilenumbrüche anstelle von Kommas getrennt sind, werden deren Inhalte *vertikal zusammengefügt*, anstatt dass die Argumente selbst als Elemente verwendet werden.

```jldoctest
julia> [1:2, 4:5] # Has a comma, so no concatenation occurs. The ranges are themselves the elements
2-element Vector{UnitRange{Int64}}:
 1:2
 4:5

julia> [1:2; 4:5]
4-element Vector{Int64}:
 1
 2
 4
 5

julia> [1:2
        4:5
        6]
5-element Vector{Int64}:
 1
 2
 4
 5
 6
```

Ähnlich, wenn die Argumente durch Tabs oder Leerzeichen oder doppelte Semikolons getrennt sind, werden ihre Inhalte *horizontal zusammengefügt*.

```jldoctest
julia> [1:2  4:5  7:8]
2×3 Matrix{Int64}:
 1  4  7
 2  5  8

julia> [[1,2]  [4,5]  [7,8]]
2×3 Matrix{Int64}:
 1  4  7
 2  5  8

julia> [1 2 3] # Numbers can also be horizontally concatenated
1×3 Matrix{Int64}:
 1  2  3

julia> [1;; 2;; 3;; 4]
1×4 Matrix{Int64}:
 1  2  3  4
```

Einzelne Semikolons (oder Zeilenumbrüche) und Leerzeichen (oder Tabs) können kombiniert werden, um sowohl horizontal als auch vertikal gleichzeitig zu verketten.

```jldoctest
julia> [1 2
        3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> [zeros(Int, 2, 2) [1; 2]
        [3 4]            5]
3×3 Matrix{Int64}:
 0  0  1
 0  0  2
 3  4  5

julia> [[1 1]; 2 3; [4 4]]
3×2 Matrix{Int64}:
 1  1
 2  3
 4  4
```

Leerzeichen (und Tabs) haben eine höhere Priorität als Semikolons, wobei zuerst alle horizontalen Verkettungen durchgeführt und dann das Ergebnis verkettet wird. Die Verwendung von doppelten Semikolons für die horizontale Verkettung hingegen führt zuerst alle vertikalen Verkettungen durch, bevor das Ergebnis horizontal verkettet wird.

```jldoctest
julia> [zeros(Int, 2, 2) ; [3 4] ;; [1; 2] ; 5]
3×3 Matrix{Int64}:
 0  0  1
 0  0  2
 3  4  5

julia> [1:2; 4;; 1; 3:4]
3×2 Matrix{Int64}:
 1  1
 2  3
 4  4
```

Genau wie `;` und `;;` in der ersten und zweiten Dimension konkateniert werden, erweitert die Verwendung von mehr Semikolons dasselbe allgemeine Schema. Die Anzahl der Semikolons im Separator gibt die jeweilige Dimension an, sodass `;;;` in der dritten Dimension konkateniert, `;;;;` in der vierten und so weiter. Weniger Semikolons haben Vorrang, sodass die niedrigeren Dimensionen in der Regel zuerst konkateniert werden.

```jldoctest
julia> [1; 2;; 3; 4;; 5; 6;;;
        7; 8;; 9; 10;; 11; 12]
2×3×2 Array{Int64, 3}:
[:, :, 1] =
 1  3  5
 2  4  6

[:, :, 2] =
 7   9  11
 8  10  12
```

Wie zuvor haben Leerzeichen (und Tabs) für die horizontale Verkettung eine höhere Priorität als jede Anzahl von Semikolons. Daher können auch höherdimensionale Arrays geschrieben werden, indem zuerst ihre Zeilen angegeben werden, wobei ihre Elemente textlich in einer Weise angeordnet sind, die ihrem Layout ähnlich ist:

```jldoctest
julia> [1 3 5
        2 4 6;;;
        7 9 11
        8 10 12]
2×3×2 Array{Int64, 3}:
[:, :, 1] =
 1  3  5
 2  4  6

[:, :, 2] =
 7   9  11
 8  10  12

julia> [1 2;;; 3 4;;;; 5 6;;; 7 8]
1×2×2×2 Array{Int64, 4}:
[:, :, 1, 1] =
 1  2

[:, :, 2, 1] =
 3  4

[:, :, 1, 2] =
 5  6

[:, :, 2, 2] =
 7  8

julia> [[1 2;;; 3 4];;;; [5 6];;; [7 8]]
1×2×2×2 Array{Int64, 4}:
[:, :, 1, 1] =
 1  2

[:, :, 2, 1] =
 3  4

[:, :, 1, 2] =
 5  6

[:, :, 2, 2] =
 7  8
```

Obwohl beide die Verkettung in der zweiten Dimension bedeuten, können Leerzeichen (oder Tabs) und `;;` nicht im selben Array-Ausdruck erscheinen, es sei denn, das doppelte Semikolon dient einfach als "Zeilenfortsetzungs"-Zeichen. Dies ermöglicht es, eine einzelne horizontale Verkettung über mehrere Zeilen zu spannen (ohne dass der Zeilenumbruch als vertikale Verkettung interpretiert wird).

```jldoctest
julia> [1 2 ;;
       3 4]
1×4 Matrix{Int64}:
 1  2  3  4
```

Beendende Semikolons können auch verwendet werden, um nachfolgende Dimensionen der Länge 1 hinzuzufügen.

```jldoctest
julia> [1;;]
1×1 Matrix{Int64}:
 1

julia> [2; 3;;;]
2×1×1 Array{Int64, 3}:
[:, :, 1] =
 2
 3
```

Allgemeiner gesagt kann die Verkettung durch die [`cat`](@ref)-Funktion erreicht werden. Diese Syntaxen sind Abkürzungen für Funktionsaufrufe, die selbst Komfortfunktionen sind:

| Syntax                 | Function         | Description                                                                                                |
|:---------------------- |:---------------- |:---------------------------------------------------------------------------------------------------------- |
|                        | [`cat`](@ref)    | concatenate input arrays along dimension(s) `k`                                                            |
| `[A; B; C; ...]`       | [`vcat`](@ref)   | shorthand for `cat(A...; dims=1)`                                                                          |
| `[A B C ...]`          | [`hcat`](@ref)   | shorthand for `cat(A...; dims=2)`                                                                          |
| `[A B; C D; ...]`      | [`hvcat`](@ref)  | simultaneous vertical and horizontal concatenation                                                         |
| `[A; C;; B; D;;; ...]` | [`hvncat`](@ref) | simultaneous n-dimensional concatenation, where number of semicolons indicate the dimension to concatenate |

### [Typed array literals](@id man-array-typed-literal)

Ein Array mit einem bestimmten Elementtyp kann mit der Syntax `T[A, B, C, ...]` erstellt werden. Dies erstellt ein 1-d Array mit dem Elementtyp `T`, das mit den Elementen `A`, `B`, `C` usw. initialisiert wird. Zum Beispiel erstellt `Any[x, y, z]` ein heterogenes Array, das beliebige Werte enthalten kann.

Die Verkettungssyntax kann ähnlich mit einem Typ vorangestellt werden, um den Elementtyp des Ergebnisses anzugeben.

```jldoctest
julia> [[1 2] [3 4]]
1×4 Matrix{Int64}:
 1  2  3  4

julia> Int8[[1 2] [3 4]]
1×4 Matrix{Int8}:
 1  2  3  4
```

## [Comprehensions](@id man-comprehensions)

Komprehensionen bieten eine allgemeine und leistungsstarke Möglichkeit, Arrays zu konstruieren. Die Syntax der Komprehension ähnelt der Mengenkonstruktion in der Mathematik:

```
A = [ F(x, y, ...) for x=rx, y=ry, ... ]
```

Die Bedeutung dieser Form ist, dass `F(x,y,...)` mit den Variablen `x`, `y` usw. ausgewertet wird, die jeweils jeden Wert in ihrer gegebenen Liste von Werten annehmen. Werte können als jedes iterierbare Objekt angegeben werden, sind jedoch häufig Bereiche wie `1:n` oder `2:(n-1)` oder explizite Arrays von Werten wie `[1.2, 3.4, 5.7]`. Das Ergebnis ist ein N-d dichter Array mit Dimensionen, die die Verkettung der Dimensionen der Variablenbereiche `rx`, `ry` usw. sind, und jede Auswertung von `F(x,y,...)` gibt einen Skalar zurück.

Das folgende Beispiel berechnet einen gewichteten Durchschnitt des aktuellen Elements sowie seines linken und rechten Nachbarn entlang eines 1-d Gitters. :

```julia-repl
julia> x = rand(8)
8-element Array{Float64,1}:
 0.843025
 0.869052
 0.365105
 0.699456
 0.977653
 0.994953
 0.41084
 0.809411

julia> [ 0.25*x[i-1] + 0.5*x[i] + 0.25*x[i+1] for i=2:length(x)-1 ]
6-element Array{Float64,1}:
 0.736559
 0.57468
 0.685417
 0.912429
 0.8446
 0.656511
```

Der resultierende Array-Typ hängt von den Typen der berechneten Elemente ab, genau wie [array literals](@ref man-array-literals) es tut. Um den Typ explizit zu steuern, kann ein Typ der Listenkonstruktion vorangestellt werden. Zum Beispiel könnten wir das Ergebnis in einfacher Präzision angefordert haben, indem wir Folgendes geschrieben haben:

```julia
Float32[ 0.25*x[i-1] + 0.5*x[i] + 0.25*x[i+1] for i=2:length(x)-1 ]
```

## [Generator Expressions](@id man-generators)

Komprehensionen können auch ohne die umschließenden eckigen Klammern geschrieben werden, was ein Objekt erzeugt, das als Generator bekannt ist. Dieses Objekt kann iteriert werden, um Werte nach Bedarf zu erzeugen, anstatt ein Array zuzuweisen und sie im Voraus zu speichern (siehe [Iteration](@ref)). Zum Beispiel summiert der folgende Ausdruck eine Reihe, ohne Speicher zuzuweisen:

```jldoctest
julia> sum(1/n^2 for n=1:1000)
1.6439345666815615
```

Beim Schreiben eines Generatorausdrucks mit mehreren Dimensionen innerhalb einer Argumentliste sind Klammern erforderlich, um den Generator von nachfolgenden Argumenten zu trennen:

```julia-repl
julia> map(tuple, 1/(i+j) for i=1:2, j=1:2, [1:4;])
ERROR: syntax: invalid iteration specification
```

Alle durch Kommas getrennten Ausdrücke nach `for` werden als Bereiche interpretiert. Das Hinzufügen von Klammern ermöglicht es uns, ein drittes Argument zu [`map`](@ref) hinzuzufügen:

```jldoctest
julia> map(tuple, (1/(i+j) for i=1:2, j=1:2), [1 3; 2 4])
2×2 Matrix{Tuple{Float64, Int64}}:
 (0.5, 1)       (0.333333, 3)
 (0.333333, 2)  (0.25, 4)
```

Generatoren werden über innere Funktionen implementiert. Genau wie innere Funktionen, die an anderen Stellen in der Sprache verwendet werden, können Variablen aus dem umgebenden Geltungsbereich in der inneren Funktion "erfasst" werden. Zum Beispiel erfasst `sum(p[i] - q[i] for i=1:n)` die drei Variablen `p`, `q` und `n` aus dem umgebenden Geltungsbereich. Erfasste Variablen können Leistungsprobleme verursachen; siehe [performance tips](@ref man-performance-captured).

Bereiche in Generatoren und Komprehensionen können von vorherigen Bereichen abhängen, indem mehrere `for`-Schlüsselwörter geschrieben werden:

```jldoctest
julia> [(i, j) for i=1:3 for j=1:i]
6-element Vector{Tuple{Int64, Int64}}:
 (1, 1)
 (2, 1)
 (2, 2)
 (3, 1)
 (3, 2)
 (3, 3)
```

In solchen Fällen ist das Ergebnis immer 1-d.

Generierte Werte können mit dem `if`-Schlüsselwort gefiltert werden:

```jldoctest
julia> [(i, j) for i=1:3 for j=1:i if i+j == 4]
2-element Vector{Tuple{Int64, Int64}}:
 (2, 2)
 (3, 1)
```

## [Indexing](@id man-array-indexing)

Die allgemeine Syntax zum Indizieren in ein n-dimensionales Array `A` ist:

```
X = A[I_1, I_2, ..., I_n]
```

wo jedes `I_k` ein skalare Ganzzahl, ein Array von Ganzzahlen oder eine andere [supported index](@ref man-supported-index-types) sein kann. Dies umfasst [`Colon`](@ref) (`:`), um alle Indizes innerhalb der gesamten Dimension auszuwählen, Bereiche der Form `a:c` oder `a:b:c`, um zusammenhängende oder gestreifte Unterabschnitte auszuwählen, und Arrays von Booleans, um Elemente an ihren `true` Indizes auszuwählen.

Wenn alle Indizes Skalare sind, dann ist das Ergebnis `X` ein einzelnes Element aus dem Array `A`. Andernfalls ist `X` ein Array mit der gleichen Anzahl von Dimensionen wie die Summe der Dimensionen aller Indizes.

Wenn alle Indizes `I_k` Vektoren sind, wäre die Form von `X` `(length(I_1), length(I_2), ..., length(I_n))`, wobei der Standort `i_1, i_2, ..., i_n` von `X` den Wert `A[I_1[i_1], I_2[i_2], ..., I_n[i_n]]` enthält.

Beispiel:

```jldoctest
julia> A = reshape(collect(1:16), (2, 2, 2, 2))
2×2×2×2 Array{Int64, 4}:
[:, :, 1, 1] =
 1  3
 2  4

[:, :, 2, 1] =
 5  7
 6  8

[:, :, 1, 2] =
  9  11
 10  12

[:, :, 2, 2] =
 13  15
 14  16

julia> A[1, 2, 1, 1] # all scalar indices
3

julia> A[[1, 2], [1], [1, 2], [1]] # all vector indices
2×1×2×1 Array{Int64, 4}:
[:, :, 1, 1] =
 1
 2

[:, :, 2, 1] =
 5
 6

julia> A[[1, 2], [1], [1, 2], 1] # a mix of index types
2×1×2 Array{Int64, 3}:
[:, :, 1] =
 1
 2

[:, :, 2] =
 5
 6
```

Beachten Sie, wie die Größe des resultierenden Arrays in den letzten beiden Fällen unterschiedlich ist.

Wenn `I_1` in eine zweidimensionale Matrix geändert wird, wird `X` zu einem `n+1`-dimensionalen Array der Form `(size(I_1, 1), size(I_1, 2), length(I_2), ..., length(I_n))`. Die Matrix fügt eine Dimension hinzu.

Beispiel:

```jldoctest
julia> A = reshape(collect(1:16), (2, 2, 2, 2));

julia> A[[1 2; 1 2]]
2×2 Matrix{Int64}:
 1  2
 1  2

julia> A[[1 2; 1 2], 1, 2, 1]
2×2 Matrix{Int64}:
 5  6
 5  6
```

Der Standort `i_1, i_2, i_3, ..., i_{n+1}` enthält den Wert bei `A[I_1[i_1, i_2], I_2[i_3], ..., I_n[i_{n+1}]]`. Alle Dimensionen, die mit Skalaren indiziert sind, werden entfernt. Zum Beispiel, wenn `J` ein Array von Indizes ist, dann ist das Ergebnis von `A[2, J, 3]` ein Array der Größe `size(J)`. Sein `j`-tes Element wird mit `A[2, J[j], 3]` befüllt.

Als ein besonderer Teil dieser Syntax kann das `end`-Schlüsselwort verwendet werden, um den letzten Index jeder Dimension innerhalb der Indizierungs-Klammern darzustellen, wie er durch die Größe des am tiefsten indizierten Arrays bestimmt wird. Die Indizierungs-Syntax ohne das `end`-Schlüsselwort ist äquivalent zu einem Aufruf von [`getindex`](@ref):

```
X = getindex(A, I_1, I_2, ..., I_n)
```

Beispiel:

```jldoctest
julia> x = reshape(1:16, 4, 4)
4×4 reshape(::UnitRange{Int64}, 4, 4) with eltype Int64:
 1  5   9  13
 2  6  10  14
 3  7  11  15
 4  8  12  16

julia> x[2:3, 2:end-1]
2×2 Matrix{Int64}:
 6  10
 7  11

julia> x[1, [2 3; 4 1]]
2×2 Matrix{Int64}:
  5  9
 13  1
```

## [Indexed Assignment](@id man-indexed-assignment)

Die allgemeine Syntax zum Zuweisen von Werten in einem n-dimensionalen Array `A` ist:

```
A[I_1, I_2, ..., I_n] = X
```

wo jedes `I_k` ein skalare Ganzzahl, ein Array von Ganzzahlen oder eine andere [supported index](@ref man-supported-index-types) sein kann. Dies umfasst [`Colon`](@ref) (`:`), um alle Indizes innerhalb der gesamten Dimension auszuwählen, Bereiche der Form `a:c` oder `a:b:c`, um zusammenhängende oder gestreifte Teilabschnitte auszuwählen, und Arrays von Booleans, um Elemente an ihren `true` Indizes auszuwählen.

Wenn alle Indizes `I_k` Ganzzahlen sind, wird der Wert an der Stelle `I_1, I_2, ..., I_n` von `A` mit dem Wert von `X`, [`convert`](@ref) überschrieben, um den [`eltype`](@ref) von `A` bei Bedarf zu aktualisieren.

Wenn ein Index `I_k` selbst ein Array ist, muss die rechte Seite `X` ebenfalls ein Array mit derselben Form wie das Ergebnis der Indizierung `A[I_1, I_2, ..., I_n]` oder ein Vektor mit derselben Anzahl von Elementen sein. Der Wert an der Stelle `I_1[i_1], I_2[i_2], ..., I_n[i_n]` von `A` wird mit dem Wert `X[i_1, i_2, ..., i_n]` überschrieben, falls erforderlich konvertiert. Der elementweise Zuweisungsoperator `.=` kann verwendet werden, um [broadcast](@ref Broadcasting) `X` über die ausgewählten Positionen zuzuweisen:

```
A[I_1, I_2, ..., I_n] .= X
```

Genau wie in [Indexing](@ref man-array-indexing) kann das Schlüsselwort `end` verwendet werden, um den letzten Index jeder Dimension innerhalb der Indizierungs-Klammern darzustellen, wie durch die Größe des Arrays bestimmt, in das zugewiesen wird. Die Indizierungszuweisungssyntax ohne das Schlüsselwort `end` entspricht einem Aufruf von [`setindex!`](@ref):

```
setindex!(A, X, I_1, I_2, ..., I_n)
```

Beispiel:

```jldoctest
julia> x = collect(reshape(1:9, 3, 3))
3×3 Matrix{Int64}:
 1  4  7
 2  5  8
 3  6  9

julia> x[3, 3] = -9;

julia> x[1:2, 1:2] = [-1 -4; -2 -5];

julia> x
3×3 Matrix{Int64}:
 -1  -4   7
 -2  -5   8
  3   6  -9
```

## [Supported index types](@id man-supported-index-types)

In dem Ausdruck `A[I_1, I_2, ..., I_n]` kann jeder `I_k` ein Skalarindex, ein Array von Skalarindizes oder ein Objekt sein, das ein Array von Skalarindizes darstellt und durch [`to_indices`](@ref) in ein solches umgewandelt werden kann:

1. Ein Skalarindex. Standardmäßig umfasst dies:

      * Nicht-boolean Ganzzahlen
      * [`CartesianIndex{N}`](@ref)s, die sich wie ein `N`-Tupel von Ganzzahlen verhalten, das sich über mehrere Dimensionen erstreckt (siehe unten für weitere Details)
2. Ein Array von Skalarindizes. Dies umfasst:

      * Vektoren und mehrdimensionale Arrays von Ganzzahlen
      * Leere Arrays wie `[]`, die keine Elemente auswählen, z.B. `A[[]]` (nicht zu verwechseln mit `A[]`)
      * Bereiche wie `a:c` oder `a:b:c`, die zusammenhängende oder gestufte Teilabschnitte von `a` bis `c` (einschließlich) auswählen.
      * Jedes benutzerdefinierte Array von Skalarindizes, das ein Subtyp von `AbstractArray` ist.
      * Arrays von `CartesianIndex{N}` (siehe unten für weitere Details)
3. Ein Objekt, das ein Array von skalaren Indizes darstellt und in ein solches umgewandelt werden kann durch [`to_indices`](@ref). Standardmäßig umfasst dies:

      * [`Colon()`](@ref) (`:`), was repräsentiert alle Indizes innerhalb einer gesamten Dimension oder über das gesamte Array.
      * Arrays von Booleans, die Elemente an ihren `true` Indizes auswählen (siehe unten für weitere Details)

Einige Beispiele:

```jldoctest
julia> A = reshape(collect(1:2:18), (3, 3))
3×3 Matrix{Int64}:
 1   7  13
 3   9  15
 5  11  17

julia> A[4]
7

julia> A[[2, 5, 8]]
3-element Vector{Int64}:
  3
  9
 15

julia> A[[1 4; 3 8]]
2×2 Matrix{Int64}:
 1   7
 5  15

julia> A[[]]
Int64[]

julia> A[1:2:5]
3-element Vector{Int64}:
 1
 5
 9

julia> A[2, :]
3-element Vector{Int64}:
  3
  9
 15

julia> A[:, 3]
3-element Vector{Int64}:
 13
 15
 17

julia> A[:, 3:3]
3×1 Matrix{Int64}:
 13
 15
 17
```

### Cartesian indices

Das spezielle `CartesianIndex{N}`-Objekt repräsentiert einen skalaren Index, der sich wie ein `N`-Tupel von Ganzzahlen verhält, das sich über mehrere Dimensionen erstreckt. Zum Beispiel:

```jldoctest cartesianindex
julia> A = reshape(1:32, 4, 4, 2);

julia> A[3, 2, 1]
7

julia> A[CartesianIndex(3, 2, 1)] == A[3, 2, 1] == 7
true
```

Allein betrachtet mag dies relativ trivial erscheinen; `CartesianIndex` fasst einfach mehrere Ganzzahlen zu einem Objekt zusammen, das einen einzelnen mehrdimensionalen Index darstellt. Wenn es jedoch mit anderen Indexierungsformen und Iteratoren kombiniert wird, die `CartesianIndex`-Objekte erzeugen, kann dies sehr eleganten und effizienten Code erzeugen. Siehe [Iteration](@ref) unten, und für einige fortgeschrittenere Beispiele siehe [this blog post on multidimensional algorithms and iteration](https://julialang.org/blog/2016/02/iteration).

Arrays von `CartesianIndex{N}` werden ebenfalls unterstützt. Sie stellen eine Sammlung von Skalaren Indizes dar, die jeweils `N` Dimensionen umfassen und eine Form des Indexierens ermöglichen, die manchmal als punktweises Indizieren bezeichnet wird. Zum Beispiel ermöglicht es den Zugriff auf die diagonalen Elemente von der ersten "Seite" von `A` von oben:

```jldoctest cartesianindex
julia> page = A[:, :, 1]
4×4 Matrix{Int64}:
 1  5   9  13
 2  6  10  14
 3  7  11  15
 4  8  12  16

julia> page[[CartesianIndex(1, 1),
             CartesianIndex(2, 2),
             CartesianIndex(3, 3),
             CartesianIndex(4, 4)]]
4-element Vector{Int64}:
  1
  6
 11
 16
```

Dies kann viel einfacher ausgedrückt werden mit [dot broadcasting](@ref man-vectorized) und indem es mit einem normalen Ganzzahlindex kombiniert wird (anstatt die erste `page` aus `A` als separaten Schritt zu extrahieren). Es kann sogar mit einem `:` kombiniert werden, um beide Diagonalen aus den beiden Seiten gleichzeitig zu extrahieren:

```jldoctest cartesianindex
julia> A[CartesianIndex.(axes(A, 1), axes(A, 2)), 1]
4-element Vector{Int64}:
  1
  6
 11
 16

julia> A[CartesianIndex.(axes(A, 1), axes(A, 2)), :]
4×2 Matrix{Int64}:
  1  17
  6  22
 11  27
 16  32
```

!!! warning
    `CartesianIndex` und Arrays von `CartesianIndex` sind nicht mit dem `end`-Schlüsselwort kompatibel, um den letzten Index einer Dimension darzustellen. Verwenden Sie `end` nicht in Indexausdrücken, die entweder `CartesianIndex` oder Arrays davon enthalten können.


### Logical indexing

Oft als logische Indizierung oder Indizierung mit einer logischen Maske bezeichnet, wählt die Indizierung durch ein boolesches Array Elemente an den Indizes aus, an denen seine Werte `true` sind. Die Indizierung durch einen booleschen Vektor `B` ist im Wesentlichen dasselbe wie die Indizierung durch den Vektor von Ganzzahlen, der von [`findall(B)`](@ref) zurückgegeben wird. Ebenso ist die Indizierung durch ein `N`-dimensionales boolesches Array im Wesentlichen dasselbe wie die Indizierung durch den Vektor von `CartesianIndex{N}`s, an denen seine Werte `true` sind. Ein logischer Index muss ein Array derselben Form wie die Dimension(en) sein, in die er indiziert, oder er muss der einzige angegebene Index sein und die Form der eindimensionalen umgeformten Ansicht des Arrays, in das er indiziert, übereinstimmen. Es ist im Allgemeinen effizienter, boolesche Arrays direkt als Indizes zu verwenden, anstatt zuerst [`findall`](@ref) aufzurufen.

```jldoctest
julia> x = reshape(1:12, 2, 3, 2)
2×3×2 reshape(::UnitRange{Int64}, 2, 3, 2) with eltype Int64:
[:, :, 1] =
 1  3  5
 2  4  6

[:, :, 2] =
 7   9  11
 8  10  12

julia> x[:, [true false; false true; true false]]
2×3 Matrix{Int64}:
 1  5   9
 2  6  10

julia> mask = map(ispow2, x)
2×3×2 Array{Bool, 3}:
[:, :, 1] =
 1  0  0
 1  1  0

[:, :, 2] =
 0  0  0
 1  0  0

julia> x[mask]
4-element Vector{Int64}:
 1
 2
 4
 8

julia> x[vec(mask)] == x[mask] # we can also index with a single Boolean vector
true
```

### Number of indices

#### Cartesian indexing

Der gewöhnliche Weg, in ein `N`-dimensionales Array zu indizieren, besteht darin, genau `N` Indizes zu verwenden; jeder Index wählt die Position(en) in seiner jeweiligen Dimension aus. Zum Beispiel wird im dreidimensionalen Array `A = rand(4, 3, 2)` der Ausdruck `A[2, 3, 1]` die Zahl in der zweiten Zeile der dritten Spalte auf der ersten "Seite" des Arrays auswählen. Dies wird oft als *kartesisches Indizieren* bezeichnet.

#### Linear indexing

Wenn genau ein Index `i` angegeben ist, repräsentiert dieser Index nicht mehr einen Standort in einer bestimmten Dimension des Arrays. Stattdessen wählt er das `i`-te Element unter Verwendung der spaltenmajoren Iterationsreihenfolge aus, die das gesamte Array linear durchläuft. Dies ist als *lineare Indizierung* bekannt. Es behandelt das Array im Wesentlichen so, als wäre es in einen eindimensionalen Vektor mit [`vec`](@ref) umgeformt worden.

```jldoctest linindexing
julia> A = [2 6; 4 7; 3 1]
3×2 Matrix{Int64}:
 2  6
 4  7
 3  1

julia> A[5]
7

julia> vec(A)[5]
7
```

Ein linearer Index in das Array `A` kann mit `CartesianIndices(A)[i]` in einen `CartesianIndex` für die kartesische Indizierung umgewandelt werden (siehe [`CartesianIndices`](@ref)), und eine Menge von `N` kartesischen Indizes kann mit `LinearIndices(A)[i_1, i_2, ..., i_N]` in einen linearen Index umgewandelt werden (siehe [`LinearIndices`](@ref)).

```jldoctest linindexing
julia> CartesianIndices(A)[5]
CartesianIndex(2, 2)

julia> LinearIndices(A)[2, 2]
5
```

Es ist wichtig zu beachten, dass es eine sehr große Asymmetrie in der Leistung dieser Konversionen gibt. Die Umwandlung eines linearen Index in eine Menge von kartesischen Indizes erfordert Division und die Berechnung des Rests, während der umgekehrte Weg nur Multiplikationen und Additionen erfordert. In modernen Prozessoren kann die ganzzahlige Division 10-50 Mal langsamer sein als die Multiplikation. Während einige Arrays — wie [`Array`](@ref) selbst — mit einem linearen Speicherblock implementiert sind und direkt einen linearen Index in ihren Implementierungen verwenden, benötigen andere Arrays — wie [`Diagonal`](@ref) — die vollständige Menge von kartesischen Indizes, um ihre Suche durchzuführen (siehe [`IndexStyle`](@ref), um zu introspektieren, welches welches ist).

!!! warning
    Beim Iterieren über alle Indizes eines Arrays ist es besser, über [`eachindex(A)`](@ref) anstelle von `1:length(A)` zu iterieren. Dies wird nicht nur schneller sein, wenn `A` `IndexCartesian` ist, sondern unterstützt auch Arrays mit benutzerdefinierter Indizierung, wie [OffsetArrays](https://github.com/JuliaArrays/OffsetArrays.jl). Wenn nur die Werte benötigt werden, ist es besser, das Array direkt zu iterieren, d.h. `for a in A`.


#### Omitted and extra indices

Neben der linearen Indizierung kann ein `N`-dimensionales Array in bestimmten Situationen mit weniger oder mehr als `N` Indizes indiziert werden.

Indizes können weggelassen werden, wenn die nachfolgenden Dimensionen, die nicht indiziert werden, alle die Länge eins haben. Mit anderen Worten, nachfolgende Indizes können nur weggelassen werden, wenn es nur einen möglichen Wert gibt, den diese weggelassenen Indizes für einen gültigen Indexausdruck haben könnten. Zum Beispiel kann ein vierdimensionales Array mit der Größe `(3, 4, 2, 1)` nur mit drei Indizes indiziert werden, da die Dimension, die übersprungen wird (die vierte Dimension), die Länge eins hat. Beachten Sie, dass die lineare Indizierung Vorrang vor dieser Regel hat.

```jldoctest
julia> A = reshape(1:24, 3, 4, 2, 1)
3×4×2×1 reshape(::UnitRange{Int64}, 3, 4, 2, 1) with eltype Int64:
[:, :, 1, 1] =
 1  4  7  10
 2  5  8  11
 3  6  9  12

[:, :, 2, 1] =
 13  16  19  22
 14  17  20  23
 15  18  21  24

julia> A[1, 3, 2] # Omits the fourth dimension (length 1)
19

julia> A[1, 3] # Attempts to omit dimensions 3 & 4 (lengths 2 and 1)
ERROR: BoundsError: attempt to access 3×4×2×1 reshape(::UnitRange{Int64}, 3, 4, 2, 1) with eltype Int64 at index [1, 3]

julia> A[19] # Linear indexing
19
```

Wenn alle Indizes mit `A[]` weggelassen werden, bietet diese Semantik ein einfaches Idiom, um das einzige Element in einem Array abzurufen und gleichzeitig sicherzustellen, dass es nur ein Element gab.

Ähnlich können mehr als `N` Indizes bereitgestellt werden, wenn alle Indizes über der Dimensionalität des Arrays `1` sind (oder allgemeiner das erste und einzige Element von `axes(A, d)` ist, wobei `d` die jeweilige Dimensionsnummer ist). Dies ermöglicht es, Vektoren wie eindimensionale Matrizen zu indizieren, zum Beispiel:

```jldoctest
julia> A = [8, 6, 7]
3-element Vector{Int64}:
 8
 6
 7

julia> A[2, 1]
6
```

## Iteration

Die empfohlenen Möglichkeiten, über ein ganzes Array zu iterieren, sind

```julia
for a in A
    # Do something with the element a
end

for i in eachindex(A)
    # Do something with i and/or A[i]
end
```

Die erste Konstruktion wird verwendet, wenn Sie den Wert, aber nicht den Index jedes Elements benötigen. In der zweiten Konstruktion wird `i` ein `Int` sein, wenn `A` ein Array-Typ mit schneller linearer Indizierung ist; andernfalls wird es ein `CartesianIndex` sein:

```jldoctest
julia> A = rand(4, 3);

julia> B = view(A, 1:3, 2:3);

julia> for i in eachindex(B)
           @show i
       end
i = CartesianIndex(1, 1)
i = CartesianIndex(2, 1)
i = CartesianIndex(3, 1)
i = CartesianIndex(1, 2)
i = CartesianIndex(2, 2)
i = CartesianIndex(3, 2)
```

!!! note
    Im Gegensatz zu `for i = 1:length(A)` bietet die Iteration mit [`eachindex`](@ref) eine effiziente Möglichkeit, über jeden Array-Typ zu iterieren. Darüber hinaus unterstützt dies auch generische Arrays mit benutzerdefinierter Indizierung wie [OffsetArrays](https://github.com/JuliaArrays/OffsetArrays.jl).


## Array traits

Wenn Sie einen benutzerdefinierten [`AbstractArray`](@ref)-Typ schreiben, können Sie angeben, dass er eine schnelle lineare Indizierung hat, indem Sie

```julia
Base.IndexStyle(::Type{<:MyArray}) = IndexLinear()
```

Diese Einstellung bewirkt, dass die `eachindex`-Iteration über ein `MyArray` Ganzzahlen verwendet. Wenn Sie dieses Merkmal nicht angeben, wird der Standardwert `IndexCartesian()` verwendet.

## [Array and Vectorized Operators and Functions](@id man-array-and-vectorized-operators-and-functions)

Die folgenden Operatoren werden für Arrays unterstützt:

1. Unäre Arithmetik – `-`, `+`
2. Binäre Arithmetik – `-`, `+`, `*`, `/`, `\`, `^`
3. Vergleich – `==`, `!=`, `≈` ([`isapprox`](@ref)), `≉`

Um eine bequeme Vektorisierung mathematischer und anderer Operationen zu ermöglichen, verwendet Julia [provides the dot syntax](@ref man-vectorized) `f.(args...)`, z.B. `sin.(x)` oder `min.(x, y)`, für elementweise Operationen über Arrays oder Mischungen aus Arrays und Skalaren (eine [Broadcasting](@ref)-Operation); diese haben den zusätzlichen Vorteil, dass sie beim Kombinieren mit anderen Punktaufrufen in eine einzige Schleife "fusionieren", z.B. `sin.(cos.(x))`.

Auch *jeder* binäre Operator unterstützt eine [dot version](@ref man-dot-operators), die auf Arrays (und Kombinationen von Arrays und Skalaren) in einer solchen [fused broadcasting operations](@ref man-vectorized) angewendet werden kann, z.B. `z .== sin.(x .* y)`.

Beachten Sie, dass Vergleiche wie `==` auf gesamten Arrays arbeiten und eine einzige boolesche Antwort liefern. Verwenden Sie Punktoperatoren wie `.==` für elementweise Vergleiche. (Für Vergleichsoperationen wie `<` ist *nur* die elementweise Version `.<` auf Arrays anwendbar.)

Beachten Sie auch den Unterschied zwischen `max.(a,b)`, welches [`broadcast`](@ref) und [`max`](@ref) elementweise über `a` und `b` anwendet, und [`maximum(a)`](@ref), welches den größten Wert innerhalb von `a` findet. Die gleiche Beziehung gilt für `min.(a, b)` und `minimum(a)`.

## Broadcasting

Es ist manchmal nützlich, elementweise binäre Operationen auf Arrays unterschiedlicher Größen durchzuführen, wie zum Beispiel das Hinzufügen eines Vektors zu jeder Spalte einer Matrix. Eine ineffiziente Möglichkeit, dies zu tun, wäre, den Vektor auf die Größe der Matrix zu replizieren:

```julia-repl
julia> a = rand(2, 1); A = rand(2, 3);

julia> repeat(a, 1, 3) + A
2×3 Array{Float64,2}:
 1.20813  1.82068  1.25387
 1.56851  1.86401  1.67846
```

Dies ist verschwenderisch, wenn die Dimensionen groß werden, daher bietet Julia [`broadcast`](@ref) an, das Singleton-Dimensionen in Array-Argumenten erweitert, um der entsprechenden Dimension im anderen Array zu entsprechen, ohne zusätzlichen Speicher zu verwenden, und die gegebene Funktion elementweise anzuwenden:

```julia-repl
julia> broadcast(+, a, A)
2×3 Array{Float64,2}:
 1.20813  1.82068  1.25387
 1.56851  1.86401  1.67846

julia> b = rand(1,2)
1×2 Array{Float64,2}:
 0.867535  0.00457906

julia> broadcast(+, a, b)
2×2 Array{Float64,2}:
 1.71056  0.847604
 1.73659  0.873631
```

[Dotted operators](@ref man-dot-operators) wie `.+` und `.*` sind gleichwertig zu `broadcast`-Aufrufen (außer dass sie fusionieren, wie [described above](@ref man-array-and-vectorized-operators-and-functions)). Es gibt auch eine [`broadcast!`](@ref)-Funktion, um ein explizites Ziel anzugeben (das auch in einer Fusionsweise über die `.=`-Zuweisung erreicht werden kann). Tatsächlich ist `f.(args...)` gleichwertig zu `broadcast(f, args...)`, was eine bequeme Syntax bietet, um jede Funktion zu broadcasten ([dot syntax](@ref man-vectorized)). Verschachtelte "Punktaufrufe" `f.(...)` (einschließlich Aufrufen von `.+` usw.) [automatically fuse](@ref man-dot-operators) in einen einzigen `broadcast`-Aufruf.

Zusätzlich ist [`broadcast`](@ref) nicht auf Arrays beschränkt (siehe die Funktionsdokumentation); es verarbeitet auch Skalare, Tupel und andere Sammlungen. Standardmäßig werden nur einige Argumenttypen als Skalare betrachtet, einschließlich (aber nicht beschränkt auf) `Number`s, `String`s, `Symbol`s, `Type`s, `Function`s und einige gängige Singletons wie `missing` und `nothing`. Alle anderen Argumente werden elementweise durchlaufen oder indiziert.

```jldoctest
julia> convert.(Float32, [1, 2])
2-element Vector{Float32}:
 1.0
 2.0

julia> ceil.(UInt8, [1.2 3.4; 5.6 6.7])
2×2 Matrix{UInt8}:
 0x02  0x04
 0x06  0x07

julia> string.(1:3, ". ", ["First", "Second", "Third"])
3-element Vector{String}:
 "1. First"
 "2. Second"
 "3. Third"
```

Manchmal möchte man einen Container (wie ein Array), der normalerweise an Broadcast teilnimmt, vor dem Verhalten des Broadcasts schützen, das darin besteht, über alle seine Elemente zu iterieren. Indem man ihn in einen anderen Container (wie ein einzelnes Element [`Tuple`](@ref)) platziert, behandelt der Broadcast ihn als einen einzelnen Wert.

```jldoctest
julia> ([1, 2, 3], [4, 5, 6]) .+ ([1, 2, 3],)
([2, 4, 6], [5, 7, 9])

julia> ([1, 2, 3], [4, 5, 6]) .+ tuple([1, 2, 3])
([2, 4, 6], [5, 7, 9])
```

## Implementation

Der Basis-Array-Typ in Julia ist der abstrakte Typ [`AbstractArray{T,N}`](@ref). Er ist parametrisiert durch die Anzahl der Dimensionen `N` und den Elementtyp `T`. [`AbstractVector`](@ref) und [`AbstractMatrix`](@ref) sind Aliase für die 1-d und 2-d Fälle. Operationen auf `AbstractArray`-Objekten werden unter Verwendung höherer Operatoren und Funktionen definiert, auf eine Weise, die unabhängig von der zugrunde liegenden Speicherung ist. Diese Operationen funktionieren im Allgemeinen korrekt als Fallback für jede spezifische Array-Implementierung.

Der `AbstractArray`-Typ umfasst alles, was vage array-ähnlich ist, und Implementierungen davon können sich erheblich von herkömmlichen Arrays unterscheiden. Zum Beispiel könnten Elemente auf Anfrage berechnet werden, anstatt gespeichert zu werden. Allerdings sollte jeder konkrete `AbstractArray{T,N}`-Typ im Allgemeinen mindestens [`size(A)`](@ref) (gibt ein `Int`-Tupel zurück), [`getindex(A, i)`](@ref) und [`getindex(A, i1, ..., iN)`](@ref getindex) implementieren; veränderbare Arrays sollten auch [`setindex!`](@ref) implementieren. Es wird empfohlen, dass diese Operationen nahezu konstante Zeitkomplexität haben, da sonst einige Array-Funktionen unerwartet langsam sein können. Konkrete Typen sollten auch typischerweise eine [`similar(A, T=eltype(A), dims=size(A))`](@ref)-Methode bereitstellen, die verwendet wird, um ein ähnliches Array für [`copy`](@ref) und andere Out-of-Place-Operationen zuzuweisen. Egal, wie ein `AbstractArray{T,N}` intern dargestellt wird, `T` ist der Typ des Objekts, das durch *ganzzahlige* Indizierung (`A[1, ..., 1]`, wenn `A` nicht leer ist) zurückgegeben wird, und `N` sollte die Länge des Tupels sein, das von [`size`](@ref) zurückgegeben wird. Für weitere Details zur Definition benutzerdefinierter `AbstractArray`-Implementierungen siehe die [array interface guide in the interfaces chapter](@ref man-interface-array).

`DenseArray` ist ein abstrakter Untertyp von `AbstractArray`, der alle Arrays umfasst, bei denen die Elemente zusammenhängend in Spalten-Hauptreihenfolge gespeichert sind (siehe [additional notes in Performance Tips](@ref man-performance-column-major)). Der Typ [`Array`](@ref) ist eine spezifische Instanz von `DenseArray`; [`Vector`](@ref) und [`Matrix`](@ref) sind Aliase für die 1-d und 2-d Fälle. Sehr wenige Operationen sind speziell für `Array` implementiert, über die hinaus, die für alle `AbstractArray`s erforderlich sind; ein Großteil der Array-Bibliothek ist in einer generischen Weise implementiert, die es allen benutzerdefinierten Arrays ermöglicht, sich ähnlich zu verhalten.

`SubArray` ist eine Spezialisierung von `AbstractArray`, die das Indizieren durch das Teilen des Speichers mit dem ursprünglichen Array anstelle einer Kopie durchführt. Ein `SubArray` wird mit der [`view`](@ref)-Funktion erstellt, die auf die gleiche Weise wie [`getindex`](@ref) (mit einem Array und einer Reihe von Indexargumenten) aufgerufen wird. Das Ergebnis von `4d61726b646f776e2e436f64652822222c2022766965772229_40726566` sieht genauso aus wie das Ergebnis von `4d61726b646f776e2e436f64652822222c2022676574696e6465782229_40726566`, mit dem Unterschied, dass die Daten an Ort und Stelle bleiben. `4d61726b646f776e2e436f64652822222c2022766965772229_40726566` speichert die Eingabe-Indexvektoren in einem `SubArray`-Objekt, das später verwendet werden kann, um das ursprüngliche Array indirekt zu indizieren. Durch das Setzen des [`@views`](@ref)-Makros vor einem Ausdruck oder Block von Code wird jeder `array[...]`-Schnitt in diesem Ausdruck in eine `SubArray`-Ansicht umgewandelt.

[`BitArray`](@ref) sind speichereffiziente "verpackte" boolesche Arrays, die jeweils ein Bit pro booleschem Wert speichern. Sie können ähnlich wie `Array{Bool}`-Arrays verwendet werden (die jeweils ein Byte pro booleschem Wert speichern) und können über `Array(bitarray)` und `BitArray(array)` jeweils in die andere Form konvertiert werden.

Ein Array ist "gestreckt", wenn es im Speicher mit gut definierten Abständen (Schritten) zwischen seinen Elementen gespeichert ist. Ein gestrecktes Array mit einem unterstützten Elementtyp kann an eine externe (nicht-Julia) Bibliothek wie BLAS oder LAPACK übergeben werden, indem einfach sein [`pointer`](@ref) und der Schritt für jede Dimension übergeben werden. Der [`stride(A, d)`](@ref) ist der Abstand zwischen den Elementen entlang der Dimension `d`. Zum Beispiel hat das eingebaute `Array`, das von `rand(5,7,2)` zurückgegeben wird, seine Elemente zusammenhängend in Spalten-Hauptreihenfolge angeordnet. Das bedeutet, dass der Schritt der ersten Dimension — der Abstand zwischen den Elementen in derselben Spalte — `1` ist:

```julia-repl
julia> A = rand(5, 7, 2);

julia> stride(A, 1)
1
```

Der Schritt der zweiten Dimension ist der Abstand zwischen den Elementen in derselben Zeile, wobei so viele Elemente übersprungen werden, wie in einer einzelnen Spalte (`5`). Ebenso erfordert das Springen zwischen den beiden "Seiten" (in der dritten Dimension) das Überspringen von `5*7 == 35` Elementen. Der [`strides`](@ref) dieses Arrays ist das Tupel dieser drei Zahlen zusammen:

```julia-repl
julia> strides(A)
(1, 5, 35)
```

In diesem speziellen Fall entspricht die Anzahl der *im Speicher* übersprungenen Elemente der Anzahl der *linearen Indizes*, die übersprungen wurden. Dies ist nur bei zusammenhängenden Arrays wie `Array` (und anderen `DenseArray`-Untertypen) der Fall und gilt nicht im Allgemeinen. Ansichten mit Bereichsindizes sind ein gutes Beispiel für *nicht zusammenhängende* gestreifte Arrays; betrachten Sie `V = @view A[1:3:4, 2:2:6, 2:-1:1]`. Diese Ansicht `V` verweist auf denselben Speicher wie `A`, überspringt jedoch einige ihrer Elemente und ordnet sie neu an. Der Schritt der ersten Dimension von `V` beträgt `3`, da wir nur jede dritte Zeile aus unserem ursprünglichen Array auswählen:

```julia-repl
julia> V = @view A[1:3:4, 2:2:6, 2:-1:1];

julia> stride(V, 1)
3
```

Diese Ansicht wählt ähnlich jede zweite Spalte aus unserem ursprünglichen `A` aus – und muss daher das Äquivalent von zwei fünf-Element-Spalten überspringen, wenn sie zwischen den Indizes in der zweiten Dimension wechselt:

```julia-repl
julia> stride(V, 2)
10
```

Die dritte Dimension ist interessant, weil ihre Reihenfolge umgekehrt ist! Um von der ersten "Seite" zur zweiten zu gelangen, muss sie *rückwärts* im Speicher gehen, und daher ist ihr Schritt in dieser Dimension negativ!

```julia-repl
julia> stride(V, 3)
-35
```

Das bedeutet, dass der `pointer` für `V` tatsächlich in die Mitte des Speicherblocks von `A` zeigt und auf Elemente sowohl rückwärts als auch vorwärts im Speicher verweist. Siehe die [interface guide for strided arrays](@ref man-interface-strided-arrays) für weitere Details zur Definition Ihrer eigenen gestuften Arrays. [`StridedVector`](@ref) und [`StridedMatrix`](@ref) sind praktische Aliase für viele der eingebauten Array-Typen, die als gestufte Arrays betrachtet werden, und ermöglichen es ihnen, auf ausgewählte spezialisierte Implementierungen zuzugreifen, die hochoptimierte BLAS- und LAPACK-Funktionen nur mit dem Pointer und den Strides aufrufen.

Es ist wichtig zu betonen, dass Schritte sich auf Offsets im Speicher und nicht auf Indizes beziehen. Wenn Sie zwischen linearer (einzelner Index) Indizierung und kartesischer (mehrdimensionaler Index) Indizierung konvertieren möchten, siehe [`LinearIndices`](@ref) und [`CartesianIndices`](@ref).
