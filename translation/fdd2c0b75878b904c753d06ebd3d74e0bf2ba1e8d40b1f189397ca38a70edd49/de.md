```
request(m::AbstractMenu; cursor=1)
```

Zeigt das Menü an und tritt in den interaktiven Modus ein. `cursor` gibt die Artikelnummer an, die für die anfängliche Cursor-Position verwendet wird. `cursor` kann entweder ein `Int` oder ein `RefValue{Int}` sein. Letzteres ist nützlich zur Beobachtung und Steuerung der Cursor-Position von außen.

Gibt `selected(m)` zurück.

!!! compat "Julia 1.6"
    Das Argument `cursor` erfordert Julia 1.6 oder höher.

