```
show(io::IO, mime, x)
```

Die [`display`](@ref) Funktionen rufen letztendlich `show` auf, um ein Objekt `x` als einen gegebenen `mime` Typ in einen gegebenen I/O Stream `io` (normalerweise ein Speicherpuffer) zu schreiben, wenn möglich. Um eine reichhaltige Multimedia-Darstellung eines benutzerdefinierten Typs `T` bereitzustellen, ist es nur notwendig, eine neue `show` Methode für `T` zu definieren, über: `show(io, ::MIME"mime", x::T) = ...`, wobei `mime` eine MIME-Typ-String ist und der Funktionskörper [`write`](@ref) (oder ähnliches) aufruft, um diese Darstellung von `x` in `io` zu schreiben. (Beachten Sie, dass die `MIME""` Notation nur literale Strings unterstützt; um `MIME` Typen flexibler zu konstruieren, verwenden Sie `MIME{Symbol("")}`.)

Zum Beispiel, wenn Sie einen `MyImage` Typ definieren und wissen, wie man ihn in eine PNG-Datei schreibt, könnten Sie eine Funktion `show(io, ::MIME"image/png", x::MyImage) = ...` definieren, um Ihre Bilder auf jedem PNG-fähigen `AbstractDisplay` (wie IJulia) anzuzeigen. Wie gewohnt, stellen Sie sicher, dass Sie `import Base.show` verwenden, um neue Methoden zur eingebauten Julia-Funktion `show` hinzuzufügen.

Technisch gesehen definiert das `MIME"mime"` Makro einen Singleton-Typ für den gegebenen `mime` String, was es uns ermöglicht, Julias Dispatch-Mechanismen auszunutzen, um zu bestimmen, wie Objekte eines bestimmten Typs angezeigt werden.

Der Standard-MIME-Typ ist `MIME"text/plain"`. Es gibt eine Fallback-Definition für `text/plain` Ausgabe, die `show` mit 2 Argumenten aufruft, sodass es nicht immer notwendig ist, eine Methode für diesen Fall hinzuzufügen. Wenn ein Typ jedoch von einer benutzerdefinierten menschenlesbaren Ausgabe profitiert, sollte `show(::IO, ::MIME"text/plain", ::T)` definiert werden. Zum Beispiel verwendet der `Day` Typ `1 day` als Ausgabe für den `text/plain` MIME-Typ und `Day(1)` als Ausgabe von `show` mit 2 Argumenten.

# Beispiele

```jldoctest
julia> struct Day
           n::Int
       end

julia> Base.show(io::IO, ::MIME"text/plain", d::Day) = print(io, d.n, " day")

julia> Day(1)
1 day
```

Containertypen implementieren im Allgemeinen `show` mit 3 Argumenten, indem sie `show(io, MIME"text/plain"(), x)` für Elemente `x` aufrufen, wobei `:compact => true` in einem [`IOContext`](@ref) gesetzt ist, das als erstes Argument übergeben wird.
