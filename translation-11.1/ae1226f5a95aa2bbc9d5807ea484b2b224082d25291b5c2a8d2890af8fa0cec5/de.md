`Text(s)`: Erstellen Sie ein Objekt, das `s` als einfachen Text rendert.

```
Text("foo")
```

Sie können auch einen Stream für große Datenmengen verwenden:

```
Text() do io
  println(io, "foo")
end
```

!!! warning
    `Text` wird derzeit exportiert, um die Abwärtskompatibilität aufrechtzuerhalten, aber dieser Export ist veraltet. Es wird empfohlen, diesen Typ als [`Docs.Text`](@ref) zu verwenden oder ihn explizit aus `Docs` zu importieren.

