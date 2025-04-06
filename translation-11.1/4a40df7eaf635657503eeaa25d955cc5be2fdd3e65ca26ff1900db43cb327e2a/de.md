```
yieldto(t::Task, arg = nothing)
```

Wechseln Sie zu der angegebenen Aufgabe. Beim ersten Wechsel zu einer Aufgabe wird die Funktion der Aufgabe ohne Argumente aufgerufen. Bei nachfolgenden Wechseln wird `arg` von dem letzten Aufruf der Aufgabe an `yieldto` zurückgegeben. Dies ist ein Low-Level-Aufruf, der nur Aufgaben wechselt, ohne Zustände oder Zeitplanung in irgendeiner Weise zu berücksichtigen. Seine Verwendung wird nicht empfohlen.
