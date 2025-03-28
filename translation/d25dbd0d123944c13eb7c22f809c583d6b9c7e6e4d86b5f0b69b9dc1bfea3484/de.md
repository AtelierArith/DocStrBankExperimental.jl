```
@everywhere [procs()] expr
```

Führen Sie einen Ausdruck unter `Main` auf allen `procs` aus. Fehler in einem der Prozesse werden in eine [`CompositeException`](@ref) gesammelt und ausgelöst. Zum Beispiel:

```
@everywhere bar = 1
```

definiert `Main.bar` auf allen aktuellen Prozessen. Alle später hinzugefügten Prozesse (zum Beispiel mit [`addprocs()`](@ref)) haben den Ausdruck nicht definiert.

Im Gegensatz zu [`@spawnat`](@ref) erfasst `@everywhere` keine lokalen Variablen. Stattdessen können lokale Variablen mit Interpolation übertragen werden:

```
foo = 1
@everywhere bar = $foo
```

Das optionale Argument `procs` ermöglicht es, eine Teilmenge aller Prozesse anzugeben, die den Ausdruck ausführen sollen.

Ähnlich wie beim Aufruf von `remotecall_eval(Main, procs, expr)`, jedoch mit zwei zusätzlichen Funktionen:

```
- `using` und `import` Anweisungen werden zuerst im aufrufenden Prozess ausgeführt, um sicherzustellen,
  dass Pakete vorcompiliert sind.
- Der aktuelle Quelldateipfad, der von `include` verwendet wird, wird an andere Prozesse weitergegeben.
```
