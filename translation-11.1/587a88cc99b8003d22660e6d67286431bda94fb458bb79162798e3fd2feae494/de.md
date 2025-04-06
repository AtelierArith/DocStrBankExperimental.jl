```
code_native([io=stdout,], f, types; syntax=:intel, debuginfo=:default, binary=false, dump_module=true)
```

Gibt die nativen Assemblieranweisungen aus, die für die Ausführung der Methode generiert werden, die der angegebenen generischen Funktion und dem Typsignatur entspricht, an `io`.

  * Setzen Sie die Assemblersyntax, indem Sie `syntax` auf `:intel` (Standard) für die Intel-Syntax oder `:att` für die AT&T-Syntax setzen.
  * Geben Sie die Ausführlichkeit der Codekommentare an, indem Sie `debuginfo` auf `:source` (Standard) oder `:none` setzen.
  * Wenn `binary` auf `true` gesetzt ist, drucken Sie auch den binären Maschinencode für jede Anweisung, die von einer abgekürzten Adresse vorangestellt wird.
  * Wenn `dump_module` auf `false` gesetzt ist, drucken Sie keine Metadaten wie rodata oder Direktiven.
  * Wenn `raw` auf `false` gesetzt ist, werden uninteressante Anweisungen (wie das Prolog der Safepoint-Funktion) weggelassen.

Siehe auch: [`@code_native`](@ref), [`code_warntype`](@ref), [`code_typed`](@ref), [`code_lowered`](@ref), [`code_llvm`](@ref).
