```
replacefield!(value, name::Symbol, expected, desired,
              [success_order::Symbol, [fail_order::Symbol=success_order]) -> (; old, success::Bool)
replacefield!(value, i::Int, expected, desired,
              [success_order::Symbol, [fail_order::Symbol=success_order]) -> (; old, success::Bool)
```

Führen Sie atomar die Operationen aus, um ein Feld auf einen bestimmten Wert zu erhalten und bedingt zu setzen.

```
y = getfield(value, name, fail_order)
ok = y === expected
if ok
    setfield!(value, name, desired, success_order)
end
return (; old = y, success = ok)
```

Wenn von der Hardware unterstützt, kann dies auf die entsprechende Hardwareanweisung optimiert werden, andernfalls wird eine Schleife verwendet.

!!! compat "Julia 1.7"
    Diese Funktion erfordert Julia 1.7 oder höher.

