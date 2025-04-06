```
__init__
```

`__init__()` 함수는 모듈이 런타임에서 처음 로드된 직후에 즉시 실행됩니다. 모듈의 모든 다른 문장이 실행된 후에 한 번 호출됩니다. 모듈을 완전히 가져온 후에 호출되기 때문에, 하위 모듈의 `__init__` 함수가 먼저 실행됩니다. `__init__`의 두 가지 전형적인 용도는 외부 C 라이브러리의 런타임 초기화 함수를 호출하고 외부 라이브러리에서 반환된 포인터와 관련된 전역 상수를 초기화하는 것입니다. 더 자세한 내용은 [모듈에 대한 매뉴얼 섹션](@ref modules)을 참조하십시오.

# 예제

```julia
const foo_data_ptr = Ref{Ptr{Cvoid}}(0)
function __init__()
    ccall((:foo_init, :libfoo), Cvoid, ())
    foo_data_ptr[] = ccall((:foo_data, :libfoo), Ptr{Cvoid}, ())
    nothing
end
```
