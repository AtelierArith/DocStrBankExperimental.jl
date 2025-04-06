```
modifyfield!(value, name::Symbol, op, x, [order::Symbol]) -> Pair
modifyfield!(value, i::Int, op, x, [order::Symbol]) -> Pair
```

함수를 `op` 적용한 후 필드를 가져오고 설정하는 작업을 원자적으로 수행합니다.

```
y = getfield(value, name)
z = op(y, x)
setfield!(value, name, z)
return y => z
```

하드웨어에서 지원하는 경우(예: 원자적 증가), 적절한 하드웨어 명령어로 최적화될 수 있으며, 그렇지 않으면 루프를 사용합니다.

!!! compat "Julia 1.7"
    이 함수는 Julia 1.7 이상이 필요합니다.

