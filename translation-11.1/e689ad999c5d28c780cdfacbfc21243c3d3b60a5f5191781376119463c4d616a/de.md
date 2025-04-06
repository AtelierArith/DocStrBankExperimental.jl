```
latex([io::IO], md)
```

Gibt den Inhalt des Markdown-Objekts `md` im LaTeX-Format aus, entweder indem in einen (optional) `io`-Stream geschrieben wird oder indem eine Zeichenkette zurückgegeben wird.

Man kann alternativ `show(io, "text/latex", md)` oder `repr("text/latex", md)` verwenden.

# Beispiele

```jldoctest
julia> latex(md"hello _world_")
"hello \\emph{world}\n\n"
```
