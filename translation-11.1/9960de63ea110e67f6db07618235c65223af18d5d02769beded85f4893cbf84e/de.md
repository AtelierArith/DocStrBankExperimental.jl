```
Core.set_binding_type!(module::Module, name::Symbol, [type::Type])
```

Setze den deklarierten Typ der Bindung `name` im Modul `module` auf `type`. Fehler, wenn die Bindung bereits einen Typ hat, der nicht äquivalent zu `type` ist. Wenn das Argument `type` fehlt, setze den Bindungstyp auf `Any`, wenn er nicht gesetzt ist, aber erzeuge keinen Fehler.

!!! compat "Julia 1.9"
    Diese Funktion erfordert Julia 1.9 oder später.

