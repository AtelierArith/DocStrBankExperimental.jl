```
fetch(t::Task)
```

Warten Sie, bis eine [`Task`](@ref) abgeschlossen ist, und geben Sie dann ihren Ergebniswert zurück. Wenn die Aufgabe mit einer Ausnahme fehlschlägt, wird eine [`TaskFailedException`](@ref) (die die fehlgeschlagene Aufgabe umschließt) ausgelöst.
