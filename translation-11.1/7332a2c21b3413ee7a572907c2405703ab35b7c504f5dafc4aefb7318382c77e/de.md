```
methodswith(typ[, Modul oder Funktion]; Supertypen::Bool=false])
```

Gibt ein Array von Methoden mit einem Argument des Typs `typ` zurück.

Das optionale zweite Argument beschränkt die Suche auf ein bestimmtes Modul oder eine bestimmte Funktion (der Standardwert sind alle obersten Module).

Wenn das Schlüsselwort `Supertypen` auf `true` gesetzt ist, werden auch Argumente mit einem übergeordneten Typ von `typ` zurückgegeben, wobei der Typ `Any` ausgeschlossen ist.

Siehe auch: [`methods`](@ref).
