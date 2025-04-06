```
put!(rr::Future, v)
```

Speichern Sie einen Wert in einer [`Future`](@ref) `rr`. `Future`s sind einmal schreibbare Remote-Referenzen. Ein `put!` auf einer bereits gesetzten `Future` wirft eine `Exception`. Alle asynchronen Remote-Aufrufe geben `Future`s zurück und setzen den Wert auf den Rückgabewert des Aufrufs nach Abschluss.
