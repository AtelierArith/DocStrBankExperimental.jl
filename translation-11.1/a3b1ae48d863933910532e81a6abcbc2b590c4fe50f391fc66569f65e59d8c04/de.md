```
@doc_str -> MD
```

Analysiere den gegebenen String als Markdown-Text, füge Zeilen- und Modulinformationen hinzu und gib ein entsprechendes [`MD`](@ref) Objekt zurück.

`@doc_str` kann in Verbindung mit dem [`Base.Docs`](@ref) Modul verwendet werden. Bitte beziehen Sie sich auch auf den Abschnitt im Handbuch über [Dokumentation](@ref man-documentation) für weitere Informationen.

# Beispiele

```
julia> s = doc"f(x) = 2*x"
  f(x) = 2*x

julia> typeof(s)
Markdown.MD

```
