```
swapfield!(value, name::Symbol, x, [order::Symbol])
swapfield!(value, i::Int, x, [order::Symbol])
```

필드를 동시에 가져오고 설정하는 작업을 원자적으로 수행합니다:

```
y = getfield(value, name)
setfield!(value, name, x)
return y
```

!!! compat "Julia 1.7"
    이 함수는 Julia 1.7 이상이 필요합니다.

