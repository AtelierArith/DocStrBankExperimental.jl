```
 isidentifier(s) -> Bool
```

Gibt zurück, ob das Symbol oder der String `s` Zeichen enthält, die als gültiger gewöhnlicher Bezeichner (nicht als binärer/unärer Operator) im Julia-Code interpretiert werden; siehe auch [`Base.isoperator`](@ref).

Intern ermöglicht Julia jede Zeichenfolge in einem `Symbol` (außer `\0`s), und Makros verwenden automatisch Variablennamen, die `#` enthalten, um Namenskonflikte mit dem umgebenden Code zu vermeiden. Damit der Parser eine Variable erkennen kann, verwendet er eine begrenzte Menge von Zeichen (die durch Unicode erheblich erweitert wird). `isidentifier()` ermöglicht es, den Parser direkt zu fragen, ob ein Symbol gültige Zeichen enthält.

# Beispiele

```jldoctest
julia> Meta.isidentifier(:x), Meta.isidentifier("1x")
(true, false)
```
