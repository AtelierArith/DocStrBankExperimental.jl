```
IOContext
```

`IOContext` bietet einen Mechanismus zum Übertragen von Ausgabekonfigurationseinstellungen zwischen [`show`](@ref) Methoden.

Kurz gesagt, es ist ein unveränderliches Wörterbuch, das eine Unterklasse von `IO` ist. Es unterstützt Standard-Wörterbuchoperationen wie [`getindex`](@ref) und kann auch als I/O-Stream verwendet werden.
