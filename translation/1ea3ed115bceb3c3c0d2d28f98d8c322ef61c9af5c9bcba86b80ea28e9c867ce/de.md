```
code_warntype([io::IO], f, types; debuginfo=:default)
```

Gibt die gesenkten und typ-inferierten ASTs für die Methoden aus, die der gegebenen generischen Funktion und dem Typsignatur zu `io` entsprechen, das standardmäßig auf `stdout` gesetzt ist. Die ASTs sind so annotiert, dass "nicht-blatt" Typen, die problematisch für die Leistung sein könnten, hervorgehoben werden (wenn Farbe verfügbar ist, in rot angezeigt). Dies dient als Warnung vor potenzieller Typinstabilität.

Nicht alle nicht-blatt Typen sind besonders problematisch für die Leistung, und die Leistungsmerkmale eines bestimmten Typs sind ein Implementierungsdetail des Compilers. `code_warntype` wird dazu neigen, Typen rot zu färben, wenn sie ein Leistungsproblem darstellen könnten, sodass einige Typen rot gefärbt sein können, auch wenn sie die Leistung nicht beeinträchtigen. Kleine Vereinigungen konkreter Typen sind normalerweise kein Problem, daher werden diese in gelb hervorgehoben.

Das Schlüsselwort-Argument `debuginfo` kann entweder `:source` oder `:none` (Standard) sein, um die Ausführlichkeit der Code-Kommentare anzugeben.

Siehe den Abschnitt [`@code_warntype`](@ref man-code-warntype) auf der Seite mit den Leistungstipps im Handbuch für weitere Informationen.

Siehe auch: [`@code_warntype`](@ref), [`code_typed`](@ref), [`code_lowered`](@ref), [`code_llvm`](@ref), [`code_native`](@ref).
