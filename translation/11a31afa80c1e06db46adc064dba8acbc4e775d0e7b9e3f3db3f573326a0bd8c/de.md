```
modifyproperty!(x, f::Symbol, op, v, order::Symbol=:not_atomic)
```

Die Syntax `@atomic op(x.f, v)` (und ihr Äquivalent `@atomic x.f op v`) gibt `modifyproperty!(x, :f, op, v, :sequentially_consistent)` zurück, wobei das erste Argument ein `getproperty`-Ausdruck sein muss und atomar modifiziert wird.

Der Aufruf von `op(getproperty(x, f), v)` muss standardmäßig einen Wert zurückgeben, der im Feld `f` des Objekts `x` gespeichert werden kann. Insbesondere wird im Gegensatz zum Standardverhalten von [`setproperty!`](@ref Base.setproperty!) die Funktion `convert` nicht automatisch aufgerufen.

Siehe auch [`modifyfield!`](@ref Core.modifyfield!) und [`setproperty!`](@ref Base.setproperty!).
