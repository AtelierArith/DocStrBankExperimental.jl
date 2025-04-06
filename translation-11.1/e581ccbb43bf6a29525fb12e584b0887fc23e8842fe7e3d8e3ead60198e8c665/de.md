```
ifelse(condition::Bool, x, y)
```

Gibt `x` zurück, wenn `condition` `true` ist, andernfalls `y`. Dies unterscheidet sich von `?` oder `if`, da es sich um eine gewöhnliche Funktion handelt, sodass alle Argumente zuerst ausgewertet werden. In einigen Fällen kann die Verwendung von `ifelse` anstelle einer `if`-Anweisung den Zweig im generierten Code eliminieren und eine höhere Leistung in engen Schleifen bieten.

# Beispiele

```jldoctest
julia> ifelse(1 > 2, 1, 2)
2
```
