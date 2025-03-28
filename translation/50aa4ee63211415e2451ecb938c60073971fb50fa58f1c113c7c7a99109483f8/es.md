```
setfieldonce!(value, name::Union{Int,Symbol}, desired,
              [success_order::Symbol, [fail_order::Symbol=success_order]) -> success::Bool
```

Realiza atómicamente las operaciones para establecer un campo a un valor dado, solo si no se había establecido previamente.

```
ok = !isdefined(value, name, fail_order)
if ok
    setfield!(value, name, desired, success_order)
end
return ok
```

!!! compat "Julia 1.11"
    Esta función requiere Julia 1.11 o posterior.

