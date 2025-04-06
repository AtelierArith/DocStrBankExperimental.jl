`HTML(s)`: Erstellen Sie ein Objekt, das `s` als HTML rendert.

```
HTML("<div>foo</div>")
```

Sie können auch einen Stream für große Datenmengen verwenden:

```
HTML() do io
  println(io, "<div>foo</div>")
end
```

!!! warning
    `HTML` wird derzeit exportiert, um die Abwärtskompatibilität aufrechtzuerhalten, aber dieser Export ist veraltet. Es wird empfohlen, diesen Typ als [`Docs.HTML`](@ref) zu verwenden oder ihn ausdrücklich aus `Docs` zu importieren.

