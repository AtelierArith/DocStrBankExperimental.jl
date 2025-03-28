```
@code_llvm
```

Bewertet die Argumente des Funktions- oder Makroaufrufs, bestimmt deren Typen und ruft [`code_llvm`](@ref) auf dem resultierenden Ausdruck auf. Setzen Sie die optionalen Schlüsselwortargumente `raw`, `dump_module`, `debuginfo`, `optimize`, indem Sie sie und ihren Wert vor dem Funktionsaufruf angeben, wie folgt:

```
@code_llvm raw=true dump_module=true debuginfo=:default f(x)
@code_llvm optimize=false f(x)
```

`optimize` steuert, ob zusätzliche Optimierungen, wie Inlining, ebenfalls angewendet werden. `raw` macht alle Metadaten und dbg.*-Aufrufe sichtbar. `debuginfo` kann entweder `:source` (Standard) oder `:none` sein, um die Ausführlichkeit der Codekommentare anzugeben. `dump_module` druckt das gesamte Modul, das die Funktion kapselt.

Siehe auch: [`code_llvm`](@ref), [`@code_warntype`](@ref), [`@code_typed`](@ref), [`@code_lowered`](@ref), [`@code_native`](@ref).
