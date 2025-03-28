```
@MIME_str
```

Ein Komfort-Makro zum Schreiben von [`MIME`](@ref) Typen, das typischerweise verwendet wird, wenn Methoden zu [`show`](@ref) hinzugefügt werden. Zum Beispiel könnte die Syntax `show(io::IO, ::MIME"text/html", x::MyType) = ...` verwendet werden, um zu definieren, wie eine HTML-Darstellung von `MyType` geschrieben wird.
