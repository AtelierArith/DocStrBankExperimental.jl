```
welches(f, typen)
```

Gibt die Methode von `f` (ein `Method`-Objekt) zurück, die für Argumente der angegebenen `typen` aufgerufen werden würde.

Wenn `typen` ein abstrakter Typ ist, wird die Methode zurückgegeben, die von `invoke` aufgerufen würde.

Siehe auch: [`parentmodule`](@ref), [`@which`](@ref Main.InteractiveUtils.@which) und [`@edit`](@ref Main.InteractiveUtils.@edit).
