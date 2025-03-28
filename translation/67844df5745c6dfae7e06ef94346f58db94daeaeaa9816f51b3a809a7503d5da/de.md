```
code_llvm([io=stdout,], f, types; raw=false, dump_module=false, optimize=true, debuginfo=:default)
```

Gibt die LLVM-Bitcodes aus, die für die Ausführung der Methode generiert wurden, die der gegebenen generischen Funktion und dem Typsignatur entspricht, an `io`.

Wenn das Schlüsselwort `optimize` nicht gesetzt ist, wird der Code vor den LLVM-Optimierungen angezeigt. Alle Metadaten und dbg.*-Aufrufe werden aus dem gedruckten Bitcode entfernt. Für das vollständige IR setzen Sie das Schlüsselwort `raw` auf true. Um das gesamte Modul, das die Funktion kapselt (mit Deklarationen), auszugeben, setzen Sie das Schlüsselwort `dump_module` auf true. Das Schlüsselwort `debuginfo` kann entweder source (Standard) oder none sein, um die Ausführlichkeit der Codekommentare anzugeben.

Siehe auch: [`@code_llvm`](@ref), [`code_warntype`](@ref), [`code_typed`](@ref), [`code_lowered`](@ref), [`code_native`](@ref).
