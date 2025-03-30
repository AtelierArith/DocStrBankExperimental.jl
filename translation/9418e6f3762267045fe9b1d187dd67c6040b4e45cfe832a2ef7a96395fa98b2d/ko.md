```
replacefield!(value, name::Symbol, expected, desired,
              [success_order::Symbol, [fail_order::Symbol=success_order]) -> (; old, success::Bool)
replacefield!(value, i::Int, expected, desired,
              [success_order::Symbol, [fail_order::Symbol=success_order]) -> (; old, success::Bool)
```

주어진 값으로 필드를 가져오고 조건부로 설정하는 작업을 원자적으로 수행합니다.

```
y = getfield(value, name, fail_order)
ok = y === expected
if ok
    setfield!(value, name, desired, success_order)
end
return (; old = y, success = ok)
```

하드웨어에서 지원하는 경우, 적절한 하드웨어 명령어로 최적화될 수 있으며, 그렇지 않으면 루프를 사용합니다.

!!! compat "Julia 1.7"
    이 함수는 Julia 1.7 이상이 필요합니다.

