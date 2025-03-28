```
atexit(f)
```

Registrieren Sie eine Null- oder Ein-Argument-Funktion `f()`, die beim Prozessausstieg aufgerufen wird. `atexit()`-Hooks werden in umgekehrter Reihenfolge (LIFO) aufgerufen und laufen vor den Objektfinalisierern.

Wenn `f` eine Methode für ein ganzzahliges Argument definiert hat, wird sie als `f(n::Int32)` aufgerufen, wobei `n` der aktuelle Exit-Code ist, andernfalls wird sie als `f()` aufgerufen.

!!! compat "Julia 1.9"
    Die Ein-Argument-Form erfordert Julia 1.9


Exit-Hooks dürfen `exit(n)` aufrufen, in diesem Fall wird Julia mit dem Exit-Code `n` (anstatt des ursprünglichen Exit-Codes) beendet. Wenn mehr als ein Exit-Hook `exit(n)` aufruft, wird Julia mit dem Exit-Code beendet, der dem zuletzt aufgerufenen Exit-Hook entspricht, der `exit(n)` aufruft. (Da Exit-Hooks in LIFO-Reihenfolge aufgerufen werden, ist "zuletzt aufgerufen" gleichbedeutend mit "zuerst registriert".)

Hinweis: Sobald alle Exit-Hooks aufgerufen wurden, können keine weiteren Exit-Hooks registriert werden, und jeder Aufruf von `atexit(f)` nach Abschluss aller Hooks wird eine Ausnahme auslösen. Diese Situation kann auftreten, wenn Sie Exit-Hooks aus Hintergrund-Tasks registrieren, die möglicherweise während des Herunterfahrens weiterhin gleichzeitig ausgeführt werden.
