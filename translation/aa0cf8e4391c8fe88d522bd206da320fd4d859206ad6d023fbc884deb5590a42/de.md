```
parse(str, start; greedy=true, raise=true, depwarn=true, filename="none")
```

Analysiere den Ausdrucksstring und gebe einen Ausdruck zurück (der später an eval zur Ausführung übergeben werden könnte). `start` ist der Codeeinheitsindex in `str` des ersten Zeichens, an dem mit dem Parsen begonnen werden soll (wie bei allen String-Indizes sind dies keine Zeichenindizes). Wenn `greedy` `true` ist (Standard), versucht `parse`, so viel Eingabe wie möglich zu konsumieren; andernfalls stoppt es, sobald es einen gültigen Ausdruck geparst hat. Unvollständige, aber ansonsten syntaktisch gültige Ausdrücke geben `Expr(:incomplete, "(Fehlermeldung)")` zurück. Wenn `raise` `true` ist (Standard), werden Syntaxfehler, die keine unvollständigen Ausdrücke sind, einen Fehler auslösen. Wenn `raise` `false` ist, gibt `parse` einen Ausdruck zurück, der bei der Auswertung einen Fehler auslöst. Wenn `depwarn` `false` ist, werden Abwertungswarnungen unterdrückt. Das Argument `filename` wird verwendet, um Diagnosen anzuzeigen, wenn ein Fehler ausgelöst wird.

```jldoctest
julia> Meta.parse("(α, β) = 3, 5", 1) # Anfang des Strings
(:((α, β) = (3, 5)), 16)

julia> Meta.parse("(α, β) = 3, 5", 1, greedy=false)
(:((α, β)), 9)

julia> Meta.parse("(α, β) = 3, 5", 16) # Ende des Strings
(nothing, 16)

julia> Meta.parse("(α, β) = 3, 5", 11) # Index von 3
(:((3, 5)), 16)

julia> Meta.parse("(α, β) = 3, 5", 11, greedy=false)
(3, 13)
```
