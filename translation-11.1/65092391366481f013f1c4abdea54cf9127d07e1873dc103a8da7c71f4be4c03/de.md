```
Symbol
```

Der Typ des Objekts, das verwendet wird, um Bezeichner in geparstem Julia-Code (ASTs) darzustellen. Wird auch oft als Name oder Etikett verwendet, um eine Entität zu identifizieren (z. B. als Schlüssel in einem Wörterbuch). `Symbol`s können mit dem `:`-Zitatoperator eingegeben werden:

```jldoctest
julia> :name
:name

julia> typeof(:name)
Symbol

julia> x = 42
42

julia> eval(:x)
42
```

`Symbol`s können auch aus Zeichenfolgen oder anderen Werten konstruiert werden, indem der Konstruktor `Symbol(x...)` aufgerufen wird.

`Symbol`s sind unveränderlich und ihre Implementierung verwendet dasselbe Objekt für alle `Symbol`s mit demselben Namen.

Im Gegensatz zu Zeichenfolgen sind `Symbol`s "atomare" oder "skalare" Entitäten, die keine Iteration über Zeichen unterstützen.
