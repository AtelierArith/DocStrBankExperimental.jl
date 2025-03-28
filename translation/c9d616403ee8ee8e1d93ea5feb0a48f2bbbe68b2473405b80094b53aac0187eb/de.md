```
fetch(x::Future)
```

Warten Sie auf und erhalten Sie den Wert eines [`Future`](@ref). Der abgerufene Wert wird lokal zwischengespeichert. Weitere Aufrufe von `fetch` auf demselben Verweis geben den zwischengespeicherten Wert zurück. Wenn der entfernte Wert eine Ausnahme ist, wird eine [`RemoteException`](@ref) ausgelöst, die die entfernte Ausnahme und den Rückverfolgungsstapel erfasst.
