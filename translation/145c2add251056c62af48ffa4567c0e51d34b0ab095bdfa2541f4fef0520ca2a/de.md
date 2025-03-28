# [Arrays with custom indices](@id man-custom-indices)

Konventionell werden Julias Arrays ab 1 indiziert, während einige andere Sprachen bei 0 zu zählen beginnen und wieder andere (z. B. Fortran) es erlauben, beliebige Startindizes anzugeben. Während es viel Sinn macht, einen Standard zu wählen (d. h. 1 für Julia), gibt es einige Algorithmen, die sich erheblich vereinfachen, wenn Sie außerhalb des Bereichs `1:size(A,d)` indizieren können (und nicht nur `0:size(A,d)-1` auch). Um solche Berechnungen zu erleichtern, unterstützt Julia Arrays mit beliebigen Indizes.

Der Zweck dieser Seite ist es, die Frage zu beantworten: "Was muss ich tun, um solche Arrays in meinem eigenen Code zu unterstützen?" Zuerst wollen wir den einfachsten Fall betrachten: Wenn Sie wissen, dass Ihr Code niemals mit Arrays mit unkonventioneller Indizierung umgehen muss, sollte die Antwort hoffentlich "nichts" sein. Alter Code, der mit konventionellen Arrays arbeitet, sollte im Wesentlichen ohne Änderungen funktionieren, solange er die exportierten Schnittstellen von Julia verwendet. Wenn Sie es für praktischer halten, Ihre Benutzer zu zwingen, traditionelle Arrays bereitzustellen, bei denen die Indizierung bei eins beginnt, können Sie hinzufügen

```julia
Base.require_one_based_indexing(arrays...)
```

wo `arrays...` eine Liste der Array-Objekte ist, die Sie auf alles überprüfen möchten, was die 1-basierte Indizierung verletzt.

## Generalizing existing code

Als Übersicht sind die Schritte:

  * Sure, please provide the Markdown content or text you'd like me to translate.
  * ersetze `1:length(A)` durch `eachindex(A)` oder in einigen Fällen `LinearIndices(A)`
  * Ersetzen Sie explizite Zuweisungen wie `Array{Int}(undef, size(B))` durch `similar(Array{Int}, axes(B))`

Diese werden weiter unten ausführlicher beschrieben.

### Things to watch out for

Weil unkonventionelles Indizieren viele Annahmen der Menschen bricht, dass alle Arrays mit 1 indiziert werden, besteht immer die Möglichkeit, dass die Verwendung solcher Arrays Fehler auslöst. Die frustrierendsten Bugs wären falsche Ergebnisse oder Segfaults (totale Abstürze von Julia). Betrachten Sie zum Beispiel die folgende Funktion:

```julia
function mycopy!(dest::AbstractVector, src::AbstractVector)
    length(dest) == length(src) || throw(DimensionMismatch("vectors must match"))
    # OK, now we're safe to use @inbounds, right? (not anymore!)
    for i = 1:length(src)
        @inbounds dest[i] = src[i]
    end
    dest
end
```

Dieser Code geht implizit davon aus, dass Vektoren von 1 indiziert werden; wenn `dest` an einem anderen Index als `src` beginnt, besteht die Möglichkeit, dass dieser Code einen Segfault auslöst. (Wenn Sie Segfaults erhalten, versuchen Sie, Julia mit der Option `--check-bounds=yes` auszuführen, um die Ursache zu lokalisieren.)

### Using `axes` for bounds checks and loop iteration

`axes(A)` (erinnert an `size(A)`) gibt ein Tupel von `AbstractUnitRange{<:Integer}`-Objekten zurück, das den Bereich der gültigen Indizes entlang jeder Dimension von `A` angibt. Wenn `A` eine unkonventionelle Indizierung hat, können die Bereiche möglicherweise nicht bei 1 beginnen. Wenn Sie nur den Bereich für eine bestimmte Dimension `d` möchten, gibt es `axes(A, d)`.

Base implementiert einen benutzerdefinierten Bereichstyp, `OneTo`, wobei `OneTo(n)` dasselbe bedeutet wie `1:n`, jedoch in einer Form, die (über das Typsystem) garantiert, dass der untere Index 1 ist. Für jeden neuen [`AbstractArray`](@ref) Typ ist dies der standardmäßig von `axes` zurückgegebene Wert, und er zeigt an, dass dieser Array-Typ eine "konventionelle" 1-basierte Indizierung verwendet.

Für die Grenzprüfung beachten Sie, dass es spezielle Funktionen `checkbounds` und `checkindex` gibt, die solche Tests manchmal vereinfachen können.

### Linear indexing (`LinearIndices`)

Einige Algorithmen lassen sich am bequemsten (oder effizientesten) in Bezug auf einen einzelnen linearen Index, `A[i]`, schreiben, selbst wenn `A` mehrdimensional ist. Unabhängig von den nativen Indizes des Arrays reichen lineare Indizes immer von `1:length(A)`. Dies wirft jedoch eine Mehrdeutigkeit für eindimensionale Arrays (auch bekannt als [`AbstractVector`](@ref)) auf: Bedeutet `v[i]` lineare Indizierung oder kartesische Indizierung mit den nativen Indizes des Arrays?

Aus diesem Grund ist es möglicherweise am besten, das Array mit `eachindex(A)` zu durchlaufen, oder, wenn Sie die Indizes als aufeinanderfolgende Ganzzahlen benötigen, den Indexbereich durch den Aufruf von `LinearIndices(A)` zu erhalten. Dies gibt `axes(A, 1)` zurück, wenn A ein AbstractVector ist, und das Äquivalent von `1:length(A)`, andernfalls.

Nach dieser Definition verwenden eindimensionale Arrays immer die kartesische Indizierung mit den nativen Indizes des Arrays. Um dies zu verdeutlichen, ist es erwähnenswert, dass die Indexkonvertierungsfunktionen einen Fehler auslösen, wenn die Form anzeigt, dass es sich um ein eindimensionales Array mit unkonventioneller Indizierung handelt (d.h. es ist ein `Tuple{UnitRange}` anstelle eines Tupels von `OneTo`). Für Arrays mit konventioneller Indizierung funktionieren diese Funktionen weiterhin wie gewohnt.

Verwenden Sie `axes` und `LinearIndices`, hier ist eine Möglichkeit, wie Sie `mycopy!` umschreiben könnten:

```julia
function mycopy!(dest::AbstractVector, src::AbstractVector)
    axes(dest) == axes(src) || throw(DimensionMismatch("vectors must match"))
    for i in LinearIndices(src)
        @inbounds dest[i] = src[i]
    end
    dest
end
```

### Allocating storage using generalizations of `similar`

Der Speicher wird oft mit `Array{Int}(undef, dims)` oder `similar(A, args...)` zugewiesen. Wenn das Ergebnis mit den Indizes eines anderen Arrays übereinstimmen muss, reicht dies möglicherweise nicht immer aus. Der generische Ersatz für solche Muster ist die Verwendung von `similar(storagetype, shape)`. `storagetype` gibt die Art des zugrunde liegenden "konventionellen" Verhaltens an, das Sie wünschen, z. B. `Array{Int}` oder `BitArray` oder sogar `dims->zeros(Float32, dims)` (was ein Array mit nur Nullen zuweisen würde). `shape` ist ein Tupel von [`Integer`](@ref) oder `AbstractUnitRange`-Werten, die die Indizes angeben, die Sie für das Ergebnis verwenden möchten. Beachten Sie, dass eine bequeme Möglichkeit, ein Array mit nur Nullen zu erzeugen, das mit den Indizes von A übereinstimmt, einfach `zeros(A)` ist.

Lass uns ein paar explizite Beispiele durchgehen. Zuerst, wenn `A` konventionelle Indizes hat, dann würde `similar(Array{Int}, axes(A))` letztendlich `Array{Int}(undef, size(A))` aufrufen und somit ein Array zurückgeben. Wenn `A` jedoch ein `AbstractArray`-Typ mit unkonventioneller Indizierung ist, sollte `similar(Array{Int}, axes(A))` etwas zurückgeben, das sich "verhält wie" ein `Array{Int}`, aber mit einer Form (einschließlich Indizes), die mit `A` übereinstimmt. (Die offensichtlichste Implementierung besteht darin, ein `Array{Int}(undef, size(A))` zuzuweisen und es dann in einen Typ zu "verpacken", der die Indizes verschiebt.)

Beachten Sie auch, dass `similar(Array{Int}, (axes(A, 2),))` einen `AbstractVector{Int}` (d.h. ein eindimensionales Array) zuweisen würde, das den Indizes der Spalten von `A` entspricht.

## Writing custom array types with non-1 indexing

Die meisten der Methoden, die Sie definieren müssen, sind standardmäßig für jeden `AbstractArray`-Typ, siehe [Abstract Arrays](@ref man-interface-array). Diese Seite konzentriert sich auf die Schritte, die erforderlich sind, um unkonventionelles Indizieren zu definieren.

### Custom `AbstractUnitRange` types

Wenn Sie einen nicht 1-indizierten Array-Typ schreiben, möchten Sie `axes` so spezialisieren, dass es einen `UnitRange` zurückgibt, oder (vielleicht besser) einen benutzerdefinierten `AbstractUnitRange`. Der Vorteil eines benutzerdefinierten Typs besteht darin, dass er den Allokationstyp für Funktionen wie `similar` "signalisiert". Wenn wir einen Array-Typ schreiben, bei dem das Indizieren bei 0 beginnt, möchten wir wahrscheinlich damit beginnen, einen neuen `AbstractUnitRange`, `ZeroRange`, zu erstellen, wobei `ZeroRange(n)` äquivalent zu `0:n-1` ist.

Im Allgemeinen sollten Sie wahrscheinlich `ZeroRange` *nicht* aus Ihrem Paket exportieren: Es kann andere Pakete geben, die ihr eigenes `ZeroRange` implementieren, und mehrere unterschiedliche `ZeroRange`-Typen zu haben, ist (vielleicht kontraintuitiv) ein Vorteil: `ModuleA.ZeroRange` zeigt an, dass `similar` ein `ModuleA.ZeroArray` erstellen sollte, während `ModuleB.ZeroRange` einen `ModuleB.ZeroArray`-Typ anzeigt. Dieses Design ermöglicht ein friedliches Zusammenleben vieler verschiedener benutzerdefinierter Array-Typen.

Beachten Sie, dass das Julia-Paket [CustomUnitRanges.jl](https://github.com/JuliaArrays/CustomUnitRanges.jl) manchmal verwendet werden kann, um die Notwendigkeit zu vermeiden, Ihren eigenen `ZeroRange`-Typ zu schreiben.

### Specializing `axes`

Sobald Sie Ihren `AbstractUnitRange`-Typ haben, spezialisieren Sie `axes`:

```julia
Base.axes(A::ZeroArray) = map(n->ZeroRange(n), A.size)
```

wo hier stellen wir uns vor, dass `ZeroArray` ein Feld namens `size` hat (es gäbe andere Möglichkeiten, dies zu implementieren).

In einigen Fällen ist die Fallback-Definition für `axes(A, d)`:

```julia
axes(A::AbstractArray{T,N}, d) where {T,N} = d <= N ? axes(A)[d] : OneTo(1)
```

möglicherweise nicht das, was Sie wollen: Sie müssen es möglicherweise spezialisieren, um etwas anderes als `OneTo(1)` zurückzugeben, wenn `d > ndims(A)`. Ebenso gibt es in `Base` eine spezielle Funktion `axes1`, die äquivalent zu `axes(A, 1)` ist, aber vermeidet, zur Laufzeit zu überprüfen, ob `ndims(A) > 0`. (Dies ist rein eine Leistungsoptimierung.) Sie ist definiert als:

```julia
axes1(A::AbstractArray{T,0}) where {T} = OneTo(1)
axes1(A::AbstractArray) = axes(A)[1]
```

Wenn der erste dieser Fälle (der nulldimensionale Fall) problematisch für Ihren benutzerdefinierten Arraytyp ist, stellen Sie sicher, dass Sie ihn entsprechend spezialisieren.

### Specializing `similar`

Angesichts Ihres benutzerdefinierten `ZeroRange`-Typs sollten Sie auch die folgenden beiden Spezialisierungen für `similar` hinzufügen:

```julia
function Base.similar(A::AbstractArray, T::Type, shape::Tuple{ZeroRange,Vararg{ZeroRange}})
    # body
end

function Base.similar(f::Union{Function,DataType}, shape::Tuple{ZeroRange,Vararg{ZeroRange}})
    # body
end
```

Beide sollten Ihren benutzerdefinierten Array-Typ zuweisen.

### Specializing `reshape`

Optionalerweise eine Methode definieren

```
Base.reshape(A::AbstractArray, shape::Tuple{ZeroRange,Vararg{ZeroRange}}) = ...
```

und Sie können ein Array `reshape` so, dass das Ergebnis benutzerdefinierte Indizes hat.

### For objects that mimic AbstractArray but are not subtypes

`has_offset_axes` hängt davon ab, dass `axes` für die Objekte, auf die Sie es anwenden, definiert ist. Wenn es einen Grund gibt, warum Sie keine `axes`-Methode für Ihr Objekt definiert haben, ziehen Sie in Betracht, eine Methode zu definieren.

```julia
Base.has_offset_axes(obj::MyNon1IndexedArraylikeObject) = true
```

Dies ermöglicht es Code, der von einer 1-basierten Indizierung ausgeht, ein Problem zu erkennen und einen hilfreichen Fehler auszugeben, anstatt falsche Ergebnisse zurückzugeben oder einen Segfault in Julia zu verursachen.

### Catching errors

Wenn Ihr neuer Array-Typ Fehler in anderem Code auslöst, kann ein hilfreicher Debugging-Schritt sein, `@boundscheck` in Ihrer `getindex`- und `setindex!`-Implementierung auszukommentieren. Dies stellt sicher, dass jeder Elementzugriff die Grenzen überprüft. Oder starten Sie Julia neu mit `--check-bounds=yes`.

In einigen Fällen kann es auch hilfreich sein, `size` und `length` vorübergehend für Ihren neuen Array-Typ zu deaktivieren, da Code, der falsche Annahmen trifft, häufig diese Funktionen verwendet.
