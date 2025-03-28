# SubArrays

Julias `SubArray`-Typ ist ein Container, der eine "Ansicht" eines übergeordneten [`AbstractArray`](@ref) kodiert. Diese Seite dokumentiert einige der Entwurfsprinzipien und die Implementierung von `SubArray`s.

Eines der Hauptziele des Designs ist es, eine hohe Leistung für Ansichten sowohl von [`IndexLinear`](@ref) als auch von [`IndexCartesian`](@ref) Arrays sicherzustellen. Darüber hinaus sollten Ansichten von `IndexLinear` Arrays, soweit es möglich ist, selbst `IndexLinear` sein.

## Index replacement

Betrachten Sie das Erstellen von 2D-Schnitten eines 3D-Arrays:

```@meta
DocTestSetup = :(import Random; Random.seed!(1234))
```

```jldoctest subarray
julia> A = rand(2,3,4);

julia> S1 = view(A, :, 1, 2:3)
2×2 view(::Array{Float64, 3}, :, 1, 2:3) with eltype Float64:
 0.839622  0.711389
 0.967143  0.103929

julia> S2 = view(A, 1, :, 2:3)
3×2 view(::Array{Float64, 3}, 1, :, 2:3) with eltype Float64:
 0.839622  0.711389
 0.789764  0.806704
 0.566704  0.962715
```

```@meta
DocTestSetup = nothing
```

`view` entfernt "Singleton"-Dimensionen (die durch ein `Int` angegeben sind), sodass sowohl `S1` als auch `S2` zweidimensionale `SubArray`s sind. Folglich ist die natürliche Art, diese zu indizieren, `S1[i,j]`. Um den Wert aus dem übergeordneten Array `A` zu extrahieren, ist der natürliche Ansatz, `S1[i,j]` durch `A[i,1,(2:3)[j]]` und `S2[i,j]` durch `A[1,i,(2:3)[j]]` zu ersetzen.

Das Hauptmerkmal des Designs von SubArrays ist, dass dieser Indexaustausch ohne jeglichen Laufzeiteinfluss durchgeführt werden kann.

## SubArray design

### Type parameters and fields

Die angenommene Strategie wird in erster Linie in der Definition des Typs ausgedrückt:

```julia
struct SubArray{T,N,P,I,L} <: AbstractArray{T,N}
    parent::P
    indices::I
    offset1::Int       # for linear indexing and pointer, only valid when L==true
    stride1::Int       # used only for linear indexing
    ...
end
```

`SubArray` hat 5 Typparameter. Die ersten beiden sind der Standardelementtyp und die Dimensionalität. Der nächste ist der Typ des übergeordneten `AbstractArray`. Der am häufigsten verwendete ist der vierte Parameter, ein `Tuple` der Typen der Indizes für jede Dimension. Der letzte, `L`, wird nur als Komfort für die Dispatch bereitgestellt; es ist ein Boolean, der darstellt, ob die Indextypen schnelles lineares Indizieren unterstützen. Mehr dazu später.

Wenn in unserem obigen Beispiel `A` ein `Array{Float64, 3}` ist, wäre unser `S1`-Fall oben ein `SubArray{Float64,2,Array{Float64,3},Tuple{Base.Slice{Base.OneTo{Int64}},Int64,UnitRange{Int64}},false}`. Beachten Sie insbesondere den Tupelparameter, der die Typen der Indizes speichert, die zur Erstellung von `S1` verwendet wurden. Ebenso,

```jldoctest subarray
julia> S1.indices
(Base.Slice(Base.OneTo(2)), 1, 2:3)
```

Das Speichern dieser Werte ermöglicht den Indexaustausch, und das Kodieren der Typen als Parameter ermöglicht es, auf effiziente Algorithmen zuzugreifen.

### Index translation

Die Durchführung der Indexübersetzung erfordert, dass man unterschiedliche Dinge für verschiedene konkrete `SubArray`-Typen tut. Zum Beispiel muss man für `S1` die `i,j`-Indizes auf die erste und dritte Dimension des übergeordneten Arrays anwenden, während man sie für `S2` auf die zweite und dritte anwenden muss. Der einfachste Ansatz zur Indizierung wäre, die Typanalyse zur Laufzeit durchzuführen:

```julia
parentindices = Vector{Any}()
for thisindex in S.indices
    ...
    if isa(thisindex, Int)
        # Don't consume one of the input indices
        push!(parentindices, thisindex)
    elseif isa(thisindex, AbstractVector)
        # Consume an input index
        push!(parentindices, thisindex[inputindex[j]])
        j += 1
    elseif isa(thisindex, AbstractMatrix)
        # Consume two input indices
        push!(parentindices, thisindex[inputindex[j], inputindex[j+1]])
        j += 2
    elseif ...
end
S.parent[parentindices...]
```

Leider wäre dies in Bezug auf die Leistung katastrophal: Jeder Elementzugriff würde Speicher zuweisen und würde die Ausführung von viel schlecht typisiertem Code beinhalten.

Der bessere Ansatz besteht darin, spezifische Methoden zu verwenden, um jeden Typ des gespeicherten Index zu behandeln. Genau das macht `reindex`: Es leitet basierend auf dem Typ des ersten gespeicherten Index weiter und verarbeitet die entsprechende Anzahl von Eingabeindizes, und dann rekursiert es über die verbleibenden Indizes. Im Fall von `S1` erweitert sich dies zu

```julia
Base.reindex(S1, S1.indices, (i, j)) == (i, S1.indices[2], S1.indices[3][j])
```

für jedes Paar von Indizes `(i,j)` (außer [`CartesianIndex`](@ref) und Arrays davon, siehe unten).

Dies ist der Kern eines `SubArray`; die Indexierungsmethoden hängen von `reindex` ab, um diese Indexübersetzung durchzuführen. Manchmal können wir jedoch die Indirektion vermeiden und es noch schneller machen.

### Linear indexing

Die lineare Indizierung kann effizient implementiert werden, wenn das gesamte Array einen einzigen Schritt hat, der aufeinanderfolgende Elemente trennt, beginnend von einem bestimmten Offset. Das bedeutet, dass wir diese Werte vorab berechnen und die lineare Indizierung einfach als Addition und Multiplikation darstellen können, wodurch die Indirektion von `reindex` und (noch wichtiger) die langsame Berechnung der kartesischen Koordinaten vollständig vermieden wird.

Für `SubArray`-Typen hängt die Verfügbarkeit einer effizienten linearen Indizierung rein von den Typen der Indizes ab und nicht von Werten wie der Größe des übergeordneten Arrays. Sie können mit der internen Funktion `Base.viewindexing` überprüfen, ob eine gegebene Menge von Indizes eine schnelle lineare Indizierung unterstützt:

```jldoctest subarray
julia> Base.viewindexing(S1.indices)
IndexCartesian()

julia> Base.viewindexing(S2.indices)
IndexLinear()
```

Dies wird während der Konstruktion des `SubArray` berechnet und im `L` Typ-Parameter als boolescher Wert gespeichert, der die Unterstützung für schnelles lineares Indizieren kodiert. Obwohl es nicht unbedingt erforderlich ist, bedeutet es, dass wir die Dispatch direkt auf `SubArray{T,N,A,I,true}` ohne Zwischeninstanzen definieren können.

Da diese Berechnung nicht von Laufzeitwerten abhängt, kann sie einige Fälle übersehen, in denen der Schritt zufällig einheitlich ist:

```jldoctest
julia> A = reshape(1:4*2, 4, 2)
4×2 reshape(::UnitRange{Int64}, 4, 2) with eltype Int64:
 1  5
 2  6
 3  7
 4  8

julia> diff(A[2:2:4,:][:])
3-element Vector{Int64}:
 2
 2
 2
```

Eine Ansicht, die als `view(A, 2:2:4, :)` konstruiert wurde, hat einen einheitlichen Schritt und daher könnte die lineare Indizierung tatsächlich effizient durchgeführt werden. Der Erfolg in diesem Fall hängt jedoch von der Größe des Arrays ab: Wenn die erste Dimension stattdessen ungerade wäre,

```jldoctest
julia> A = reshape(1:5*2, 5, 2)
5×2 reshape(::UnitRange{Int64}, 5, 2) with eltype Int64:
 1   6
 2   7
 3   8
 4   9
 5  10

julia> diff(A[2:2:4,:][:])
3-element Vector{Int64}:
 2
 3
 2
```

Dann hat `A[2:2:4,:]` keinen einheitlichen Schritt, sodass wir eine effiziente lineare Indizierung nicht garantieren können. Da wir diese Entscheidung ausschließlich auf den in den Parametern des `SubArray` kodierten Typen basieren müssen, kann `S = view(A, 2:2:4, :)` keine effiziente lineare Indizierung implementieren.

### A few details

  * Beachten Sie, dass die Funktion `Base.reindex` unabhängig von den Typen der Eingabeindizes ist; sie bestimmt einfach, wie und wo die gespeicherten Indizes neu indiziert werden sollen. Sie unterstützt nicht nur ganzzahlige Indizes, sondern auch nicht-skalare Indizierung. Das bedeutet, dass Ansichten von Ansichten keine zwei Ebenen der Indirektion benötigen; sie können einfach die Indizes in das ursprüngliche übergeordnete Array neu berechnen!
  * Hoffentlich ist es mittlerweile ziemlich klar, dass die Unterstützung von Slices bedeutet, dass die Dimensionalität, die durch den Parameter `N` gegeben ist, nicht unbedingt mit der Dimensionalität des übergeordneten Arrays oder der Länge des `indices`-Tupels übereinstimmt. Auch müssen die vom Benutzer bereitgestellten Indizes nicht unbedingt mit den Einträgen im `indices`-Tupel übereinstimmen (z. B. könnte der zweite vom Benutzer bereitgestellte Index der dritten Dimension des übergeordneten Arrays und dem dritten Element im `indices`-Tupel entsprechen).

    Was weniger offensichtlich sein könnte, ist, dass die Dimensionalität des gespeicherten Elternarrays gleich der Anzahl der effektiven Indizes im `indices`-Tupel sein muss. Einige Beispiele:

    ```julia
    A = reshape(1:35, 5, 7) # A 2d parent Array
    S = view(A, 2:7)         # A 1d view created by linear indexing
    S = view(A, :, :, 1:1)   # Appending extra indices is supported
    ```

    Naiv, würde man denken, man könnte einfach `S.parent = A` und `S.indices = (:,:,1:1)` setzen, aber dies unterstützt die Reindexierung dramatisch und kompliziert den Prozess, insbesondere bei Ansichten von Ansichten. Man muss nicht nur die Typen der gespeicherten Indizes berücksichtigen, sondern auch prüfen, ob ein gegebener Index der letzte ist und alle verbleibenden gespeicherten Indizes "zusammenführen". Dies ist keine einfache Aufgabe, und noch schlimmer: es ist langsam, da es implizit von der linearen Indizierung abhängt.

    Glücklicherweise ist dies genau die Berechnung, die `ReshapedArray` durchführt, und es tut dies linear, wenn möglich. Folglich stellt `view` sicher, dass das übergeordnete Array die geeignete Dimension für die gegebenen Indizes hat, indem es es bei Bedarf umformt. Der innere `SubArray`-Konstruktor stellt sicher, dass diese Invarianz erfüllt ist.
  * [`CartesianIndex`](@ref) und Arrays davon werfen einen unangenehmen Schraubenschlüssel in das `reindex`-Schema. Erinnern Sie sich daran, dass `reindex` einfach basierend auf dem Typ der gespeicherten Indizes dispatcht, um zu bestimmen, wie viele übergebene Indizes verwendet werden sollten und wo sie platziert werden sollten. Aber mit `CartesianIndex` gibt es keine Eins-zu-eins-Korrespondenz mehr zwischen der Anzahl der übergebenen Argumente und der Anzahl der Dimensionen, in die sie indizieren. Wenn wir zum obigen Beispiel von `Base.reindex(S1, S1.indices, (i, j))` zurückkehren, können Sie sehen, dass die Erweiterung für `i, j = CartesianIndex(), CartesianIndex(2,1)` falsch ist. Es sollte den `CartesianIndex()` vollständig *überspringen* und zurückgeben:

    ```julia
    (CartesianIndex(2,1)[1], S1.indices[2], S1.indices[3][CartesianIndex(2,1)[2]])
    ```

    Stattdessen erhalten wir jedoch:

    ```julia
    (CartesianIndex(), S1.indices[2], S1.indices[3][CartesianIndex(2,1)])
    ```

    Das korrekt zu machen würde *kombinierte* Dispatch auf sowohl den gespeicherten als auch den übergebenen Indizes über alle Kombinationen von Dimensionen in unlösbarer Weise erfordern. Daher darf `reindex` niemals mit `CartesianIndex`-Indizes aufgerufen werden. Glücklicherweise kann der skalare Fall leicht behandelt werden, indem die `CartesianIndex`-Argumente zuerst in einfache Ganzzahlen umgewandelt werden. Arrays von `CartesianIndex` hingegen können nicht so einfach in orthogonale Teile zerlegt werden. Bevor versucht wird, `reindex` zu verwenden, muss `view` sicherstellen, dass sich keine Arrays von `CartesianIndex` in der Argumentliste befinden. Wenn dies der Fall ist, kann es einfach "ablenken", indem die Berechnung von `reindex` ganz vermieden wird und stattdessen ein geschachteltes `SubArray` mit zwei Ebenen der Indirektion konstruiert wird.
