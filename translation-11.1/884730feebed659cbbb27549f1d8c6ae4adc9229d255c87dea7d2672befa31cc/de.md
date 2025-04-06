```
setprecision([T=BigFloat,] precision::Int; base=2)
```

Setzen Sie die Präzision (in Bits, standardmäßig) für die Verwendung in der Arithmetik von `T`. Wenn `base` angegeben ist, dann ist die Präzision das Minimum, das erforderlich ist, um mindestens `precision` Ziffern in der angegebenen `base` zu erhalten.

!!! warning
    Diese Funktion ist nicht threadsicher. Sie wirkt sich auf den Code aus, der auf allen Threads ausgeführt wird, aber ihr Verhalten ist undefiniert, wenn sie gleichzeitig mit Berechnungen aufgerufen wird, die die Einstellung verwenden.


!!! compat "Julia 1.8"
    Das Schlüsselwort `base` erfordert mindestens Julia 1.8.

