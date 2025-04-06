```
setfieldonce!(value, name::Union{Int,Symbol}, desired,
              [success_order::Symbol, [fail_order::Symbol=success_order]) -> success::Bool
```

주어진 값을 필드에 설정하는 작업을 원자적으로 수행하며, 이전에 설정되지 않은 경우에만 수행합니다.

```
ok = !isdefined(value, name, fail_order)
if ok
    setfield!(value, name, desired, success_order)
end
return ok
```

!!! compat "Julia 1.11"
    이 함수는 Julia 1.11 이상이 필요합니다.

