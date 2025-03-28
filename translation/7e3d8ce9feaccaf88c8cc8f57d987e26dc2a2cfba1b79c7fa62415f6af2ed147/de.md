```
Sys.isbsd([os])
```

Prädikat zum Testen, ob das Betriebssystem ein Derivat von BSD ist. Siehe Dokumentation in [Handling Operating System Variation](@ref).

!!! Hinweis     Der Darwin-Kernel stammt von BSD ab, was bedeutet, dass `Sys.isbsd()` auf macOS-Systemen `true` ist. Um macOS von einem Prädikat auszuschließen, verwenden Sie `Sys.isbsd() && !Sys.isapple()`.
