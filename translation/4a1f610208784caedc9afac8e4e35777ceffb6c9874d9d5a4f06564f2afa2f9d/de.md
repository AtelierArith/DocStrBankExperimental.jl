```
current_exceptions(task::Task=current_task(); [backtrace::Bool=true])
```

Holen Sie den Stapel der derzeit behandelten Ausnahmen ab. Bei geschachtelten Catch-Blöcken kann es mehr als eine aktuelle Ausnahme geben, wobei die zuletzt geworfene Ausnahme zuletzt im Stapel steht. Der Stapel wird als `ExceptionStack` zurückgegeben, das ein AbstractVector von benannten Tupeln `(exception,backtrace)` ist. Wenn `backtrace` falsch ist, wird der Backtrace in jedem Paar auf `nothing` gesetzt.

Das explizite Übergeben von `task` gibt den aktuellen Ausnahme-Stapel für eine beliebige Aufgabe zurück. Dies ist nützlich, um Aufgaben zu inspizieren, die aufgrund von nicht behandelten Ausnahmen fehlgeschlagen sind.

!!! compat "Julia 1.7"
    Diese Funktion trug in Julia 1.1–1.6 den experimentellen Namen `catch_stack()` und hatte einen einfachen Vector von Tupeln als Rückgabetyp.

