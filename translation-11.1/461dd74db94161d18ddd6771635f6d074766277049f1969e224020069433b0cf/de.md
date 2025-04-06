```
setrounding(T, mode)
```

Setzen Sie den Rundungsmodus des Fließkommatyps `T`, der die Rundung grundlegender arithmetischer Funktionen ([`+`](@ref), [`-`](@ref), [`*`](@ref), [`/`](@ref) und [`sqrt`](@ref)) und die Typkonvertierung steuert. Andere numerische Funktionen können falsche oder ungültige Werte zurückgeben, wenn Rundungsmodi verwendet werden, die von der Standard-[`RoundNearest`](@ref) abweichen.

Bitte beachten Sie, dass dies derzeit nur für `T == BigFloat` unterstützt wird.

!!! warning
    Diese Funktion ist nicht threadsicher. Sie wirkt sich auf den Code aus, der auf allen Threads ausgeführt wird, aber ihr Verhalten ist undefiniert, wenn sie gleichzeitig mit Berechnungen aufgerufen wird, die die Einstellung verwenden.

