```
html([io::IO], md)
```

Geben Sie den Inhalt des Markdown-Objekts `md` im HTML-Format aus, indem Sie entweder in einen (optional) `io`-Stream schreiben oder einen String zurückgeben.

Alternativ kann man `show(io, "text/html", md)` oder `repr("text/html", md)` verwenden, die sich darin unterscheiden, dass sie die Ausgabe in ein `<div class="markdown"> ... </div>`-Element einfügen.

# Beispiele

```jldoctest
julia> html(md"hello _world_")
"<p>hello <em>world</em></p>\n"
```
