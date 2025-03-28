```
Threads.maxthreadid() -> Int
```

Erhalten Sie eine untere Schranke für die Anzahl der Threads (über alle Thread-Pools) verfügbar für den Julia-Prozess, mit atomaren Erwerbssemantiken. Das Ergebnis wird immer größer oder gleich [`threadid()`](@ref) sowie `threadid(task)` für jede Aufgabe sein, die Sie beobachten konnten, bevor Sie `maxthreadid` aufgerufen haben.
