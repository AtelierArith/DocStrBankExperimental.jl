```
setfieldonce!(value, name::Union{Int,Symbol}, desired,
              [success_order::Symbol, [fail_order::Symbol=success_order]) -> success::Bool
```

Führen Sie atomar die Operationen aus, um ein Feld auf einen bestimmten Wert zu setzen, nur wenn es zuvor nicht gesetzt war.

```
ok = !isdefined(value, name, fail_order)
if ok
    setfield!(value, name, desired, success_order)
end
return ok
```

!!! compat "Julia 1.11"
    Diese Funktion erfordert Julia 1.11 oder höher.

