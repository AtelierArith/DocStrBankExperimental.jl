```
@code_native
```

Bewertet die Argumente des Funktions- oder Makroaufrufs, bestimmt deren Typen und ruft [`code_native`](@ref) auf dem resultierenden Ausdruck auf.

Setzen Sie beliebige optionale Schlüsselwortargumente `syntax`, `debuginfo`, `binary` oder `dump_module`, indem Sie sie vor dem Funktionsaufruf angeben, wie folgt:

```
@code_native syntax=:intel debuginfo=:default binary=true dump_module=false f(x)
```

  * Setzen Sie die Assemblersyntax, indem Sie `syntax` auf `:intel` (Standard) für Intel-Syntax oder `:att` für AT&T-Syntax setzen.
  * Geben Sie die Ausführlichkeit der Codekommentare an, indem Sie `debuginfo` auf `:source` (Standard) oder `:none` setzen.
  * Wenn `binary` `true` ist, drucken Sie auch den binären Maschinencode für jede Anweisung, die von einer abgekürzten Adresse vorangestellt wird.
  * Wenn `dump_module` `false` ist, drucken Sie keine Metadaten wie rodata oder Direktiven.

Siehe auch: [`code_native`](@ref), [`@code_warntype`](@ref), [`@code_typed`](@ref), [`@code_lowered`](@ref), [`@code_llvm`](@ref).
