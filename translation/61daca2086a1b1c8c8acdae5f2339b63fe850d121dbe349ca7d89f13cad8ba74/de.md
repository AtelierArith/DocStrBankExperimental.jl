```
isdone(itr, [state]) -> Union{Bool, Missing}
```

Diese Funktion bietet einen Schnellpfad-Hinweis für den Abschluss von Iteratoren. Dies ist nützlich für zustandsbehaftete Iteratoren, die vermeiden möchten, dass Elemente konsumiert werden, wenn sie nicht dem Benutzer angezeigt werden (z. B. beim Überprüfen auf Vollständigkeit in `isempty` oder `zip`).

Zustandsbehaftete Iteratoren, die diese Funktion nutzen möchten, sollten eine `isdone`-Methode definieren, die je nach Zustand des Iterators true/false zurückgibt. Zustandslose Iteratoren müssen diese Funktion nicht implementieren.

Wenn das Ergebnis `missing` ist, können die Aufrufer `iterate(x, state) === nothing` berechnen, um eine definitive Antwort zu erhalten.

Siehe auch [`iterate`](@ref), [`isempty`](@ref)
