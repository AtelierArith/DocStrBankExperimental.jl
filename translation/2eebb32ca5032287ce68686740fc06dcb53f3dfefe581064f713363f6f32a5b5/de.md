```
lookup(pointer::Ptr{Cvoid}) -> Vector{StackFrame}
```

Gibt einen Zeiger auf einen Ausführungskontext (normalerweise erzeugt durch einen Aufruf von `backtrace`) an, um Informationen zum Kontext des Stack-Frames zu suchen. Gibt ein Array von Frame-Informationen für alle an diesem Punkt inlineden Funktionen zurück, wobei die innerste Funktion zuerst kommt.
