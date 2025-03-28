```
Base.depwarn(msg::String, funcsym::Symbol; force=false)
```

Drucke `msg` als eine Abwärtskompatibilitätswarnung. Das Symbol `funcsym` sollte der Name der aufrufenden Funktion sein, die verwendet wird, um sicherzustellen, dass die Abwärtskompatibilitätswarnung nur beim ersten Mal für jeden Aufrufort gedruckt wird. Setze `force=true`, um die Warnung immer anzuzeigen, selbst wenn Julia mit `--depwarn=no` (dem Standard) gestartet wurde.

Siehe auch [`@deprecate`](@ref).

# Beispiele

```julia
function deprecated_func()
    Base.depwarn("Verwende nicht `deprecated_func()`!", :deprecated_func)

    1 + 1
end
```
