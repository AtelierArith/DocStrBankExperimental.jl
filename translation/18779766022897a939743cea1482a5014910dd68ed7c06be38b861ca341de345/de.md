```
parse(str; raise=true, depwarn=true, filename="none")
```

Analysiere den Ausdrucksstring gierig und gebe einen einzelnen Ausdruck zurück. Ein Fehler wird ausgelöst, wenn nach dem ersten Ausdruck zusätzliche Zeichen vorhanden sind. Wenn `raise` `true` ist (Standard), werden Syntaxfehler einen Fehler auslösen; andernfalls gibt `parse` einen Ausdruck zurück, der bei der Auswertung einen Fehler auslöst. Wenn `depwarn` `false` ist, werden Abwertungswarnungen unterdrückt. Das Argument `filename` wird verwendet, um Diagnosen anzuzeigen, wenn ein Fehler ausgelöst wird.

```jldoctest; filter=r"(?<=Expr\(:error).*|(?<=Expr\(:incomplete).*"
julia> Meta.parse("x = 3")
:(x = 3)

julia> Meta.parse("1.0.2")
ERROR: ParseError:
# Fehler @ none:1:1
1.0.2
└──┘ ── ungültige numerische Konstante
[...]

julia> Meta.parse("1.0.2"; raise = false)
:($(Expr(:error, "ungültige numerische Konstante "1.0."")))

julia> Meta.parse("x = ")
:($(Expr(:incomplete, "unvollständig: vorzeitiges Ende der Eingabe")))
```
