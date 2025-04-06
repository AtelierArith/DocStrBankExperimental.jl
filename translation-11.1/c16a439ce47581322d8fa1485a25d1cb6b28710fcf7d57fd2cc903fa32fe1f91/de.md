```
display(x)
display(d::AbstractDisplay, x)
display(mime, x)
display(d::AbstractDisplay, mime, x)
```

Zeige `x` mit der obersten anwendbaren Anzeige im Anzeige-Stack an, typischerweise unter Verwendung der reichhaltigsten unterstützten Multimedia-Ausgabe für `x`, wobei die einfache Textausgabe [`stdout`](@ref) als Fallback dient. Die Variante `display(d, x)` versucht, `x` nur auf der angegebenen Anzeige `d` anzuzeigen und wirft einen [`MethodError`](@ref), wenn `d` Objekte dieses Typs nicht anzeigen kann.

Im Allgemeinen kann man nicht davon ausgehen, dass die Ausgabe von `display` an `stdout` geht (im Gegensatz zu [`print(x)`](@ref) oder [`show(x)`](@ref)). Zum Beispiel kann `display(x)` ein separates Fenster mit einem Bild öffnen. `display(x)` bedeutet "zeige `x` auf die beste Weise, die du für das aktuelle Ausgabegerät(e) kannst." Wenn du eine REPL-ähnliche Textausgabe möchtest, die garantiert an `stdout` geht, verwende stattdessen [`show(stdout, "text/plain", x)`](@ref).

Es gibt auch zwei Varianten mit einem `mime`-Argument (einem MIME-Typ-String, wie `"image/png"`), die versuchen, `x` nur mit dem angeforderten MIME-Typ anzuzeigen, und einen `MethodError` werfen, wenn dieser Typ von den Anzeigen oder von `x` nicht unterstützt wird. Mit diesen Varianten kann man auch die "rohen" Daten im angeforderten MIME-Typ bereitstellen, indem man `x::AbstractString` (für MIME-Typen mit textbasierter Speicherung, wie text/html oder application/postscript) oder `x::Vector{UInt8}` (für binäre MIME-Typen) übergibt.

Um anzupassen, wie Instanzen eines Typs angezeigt werden, überlade [`show`](@ref) anstelle von `display`, wie im Handbuchabschnitt über [benutzerdefiniertes hübsches Drucken](@ref man-custom-pretty-printing) erklärt.
